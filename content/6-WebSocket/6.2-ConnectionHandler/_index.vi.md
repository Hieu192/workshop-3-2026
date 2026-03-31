---
title : "Tạo Connection Handler"
date :  2025
weight : 2 
chapter : false
pre : " <b> 6.2 </b> "
---

#### Tạo Lambda Connection Handler

Hàm này sẽ thực hiện việc lưu (khi có kết nối) và xóa (khi ngắt kết nối) thông tin kết nối vào bảng vừa tạo ở bước 6.1.

1. Truy cập dịch vụ **AWS Lambda** -> **Create function**.
![Lambda Create Connection](/images/6-2/0001.png)
![Lambda Create Connection](/images/6-2/0002.png)
2. **Function name**: `WebSocketConnectionHandler`. Runtime: `Python 3.12`.
![Lambda Create Connection](/images/6-2/0003.png)
3. Nhấn **Create function**.
![Lambda Create Connection](/images/6-2/0004.png)
4. Ở phần Code, dán đoạn mã xử lý kết nối. Bạn có thể tìm thấy mã nguồn này trong file `infra/modules/simple_websocket.py`. Bấm **Deploy**

```
import json
import boto3
import logging

logger = logging.getLogger()
logger.setLevel(logging.INFO)

dynamodb = boto3.resource('dynamodb')
connections_table = dynamodb.Table('simple-websocket-connections')

def lambda_handler(event, context):
    request_context = event.get('requestContext', {})
    route_key = request_context.get('routeKey')
    connection_id = request_context.get('connectionId')
    
    logger.info(f"Route: {route_key}, Connection: {connection_id}")
    
    try:
        if route_key == '$connect':
            connections_table.put_item(Item={'connectionId': connection_id})
            logger.info(f"Stored connection {connection_id}")
        elif route_key == '$disconnect':
            connections_table.delete_item(Key={'connectionId': connection_id})
            logger.info(f"Removed connection {connection_id}")
            
        return {'statusCode': 200, 'body': 'Connected.'}
    except Exception as e:
        logger.error(f"Error: {str(e)}")
        return {'statusCode': 500, 'body': str(e)}

```
![Lambda Create Connection](/images/6-2/0005.png)
5. Cấp quyền: Vào tab **Configuration** -> **Permissions** để cấp quyền cho Lambda được thao tác trên bảng `simple-websocket-connections`. Nhấn vào link Role (thường có dạng `WebSocketConnectionHandler-role-xxxx`, trong đó `xxxx` là các ký tự ngẫu nhiên của AWS) để mở giao diện quản lý IAM Role.
![Lambda Create Connection](/images/6-2/0006.png)

6. Tại tab Permissions, nhấn nút Add permissions -> chọn Create inline policy. Chọn tab JSON và dán đoạn mã sau (nhớ thay đổi ARN của bảng cho phù hợp) rồi nhấn **Next**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:PutItem",
                "dynamodb:DeleteItem"
            ],
            "Resource": "arn:aws:dynamodb:ap-southeast-1:423945942413:table/simple-websocket-connections"
        }
    ]
}

```
![Lambda Create Connection](/images/6-2/0007.png)
![Lambda Create Connection](/images/6-2/0008.png)
7. Đặt tên policy là `LambdaWebSocketPolicy` và nhấn **Create policy**
![Lambda Create Connection](/images/6-2/0009.png)



