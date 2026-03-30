---
title : "Tạo Stream Processor"
date :  2025
weight : 4
chapter : false
pre : " <b> 6.4 </b> "
---

#### Tạo Stream Processor

Đây là cầu nối quan trọng: Khi tin nhắn được xử lý xong (trạng thái đổi), DynamoDB Streams sẽ kích hoạt hàm này để gửi dữ liệu xuống tất cả các WebSocket đang kết nối.

1. Tạo một Lambda function thứ hai tên là `StreamProcessor` (Python 3.12).
![Lambda Stream Trigger](/images/6-4/0001.png)
![Lambda Stream Trigger](/images/6-4/0002.png)
![Lambda Stream Trigger](/images/6-4/0003.png)
2. Dán mã nguồn từ file `infra/modules/simple_websocket.py` (Mã này nhận sự kiện từ DynamoDB Streams, sau đó vòng lặp qua `simple-websocket-connections` và gọi lệnh `post_to_connection` của API Gateway).
```
import json
import boto3
import logging
import os
from botocore.exceptions import ClientError

logger = logging.getLogger()
logger.setLevel(logging.INFO)

def lambda_handler(event, context):
    dynamodb = boto3.resource('dynamodb')
    connections_table = dynamodb.Table('simple-websocket-connections')
    
    api_id = os.environ['API_ID'].strip()
    region = os.environ['AWS_REGION']
    endpoint_url = f"https://{api_id}.execute-api.{region}.amazonaws.com/prod"
    
    apigateway = boto3.client('apigatewaymanagementapi', endpoint_url=endpoint_url)
    
    # 1. Lấy danh sách kết nối
    try:
        response = connections_table.scan()
        connections = response.get('Items', [])
        logger.info(f"Tìm thấy {len(connections)} kết nối đang online")
    except Exception as e:
        logger.error(f"Lỗi khi SCAN bảng: {str(e)}")
        return
        
    # 2. Xử lý từng bản ghi thay đổi
    for record in event['Records']:
        event_name = record['eventName']
        
        # CHUYỂN ĐỔI DỮ LIỆU SANG JSON SẠCH (Rất quan trọng cho React)
        raw_data = record['dynamodb'].get('NewImage', record['dynamodb'].get('OldImage'))
        clean_data = convert_dynamodb_to_json(raw_data)
        
        change_data = {
            'eventName': event_name,
            'data': clean_data
        }
        
        # 3. Gửi tin nhắn
        for conn in connections:
            conn_id = conn['connectionId']
            try:
                apigateway.post_to_connection(ConnectionId=conn_id, Data=json.dumps(change_data))
                logger.info(f"Gửi thành công {event_name} tới {conn_id}")
            except Exception as e:
                logger.error(f"Lỗi khi gửi tới {conn_id}: {str(e)}")

    logger.info("--- KẾT THÚC XỬ LÝ ---")

def convert_dynamodb_to_json(dynamodb_item):
    """Hàm này giúp xóa các ký tự {S}, {N} để React không bị crash"""
    def convert_value(value):
        if 'S' in value: return value['S']
        elif 'N' in value: return float(value['N']) if '.' in value['N'] else int(value['N'])
        elif 'BOOL' in value: return value['BOOL']
        elif 'NULL' in value: return None
        elif 'L' in value: return [convert_value(v) for v in value['L']]
        elif 'M' in value: return {k: convert_value(v) for k, v in value['M'].items()}
        return value
    return {k: convert_value(v) for k, v in dynamodb_item.items()}

```
![Lambda Stream Trigger](/images/6-4/0004.png)


3. Cấp quyền: Lambda này cần quyền `execute-api:ManageConnections`, `dynamodb:GetRecords`, `dynamodb:GetShardIterator`, `dynamodb:DescribeStream`, `dynamodb:ListStreams` để gửi tin nhắn thông qua API Gateway, đọc DynamoDB Streams.
![Lambda Stream Trigger](/images/6-4/0005.png)
![Lambda Stream Trigger](/images/6-4/0006.png)
![Lambda Stream Trigger](/images/6-4/0007.png)
![Lambda Stream Trigger](/images/6-4/0008.png)

    - Cấp thêm quyền StreamProcessorPolicy
```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": "execute-api:ManageConnections",
			"Resource": "arn:aws:execute-api:ap-southeast-1:423945942413:kvtige2lb3/prod/POST/@connections/*"
		}
	]
}
```
![Lambda Stream Trigger](/images/6-4/0012.png)
![Lambda Stream Trigger](/images/6-4/0013.png)

4. **Thêm Trigger**: Nhấn **Add trigger** -> Chọn **DynamoDB** -> Chọn bảng `PriorityItemsTable` (bảng tạo ở Phần 1).
![Lambda Stream Trigger](/images/6-4/0009.png)
![Lambda Stream Trigger](/images/6-4/0010.png)
![Lambda Stream Trigger](/images/6-4/0011.png)
