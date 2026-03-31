---
title : "Create Connection Handler"
date :  2025
weight : 2 
chapter : false
pre : " <b> 6.2 </b> "
---

#### Create Lambda Connection Handler

This function will store (when a connection is made) and delete (when the connection is closed) the connection information in the table created in step 6.1.

1. Access the **AWS Lambda** service -> **Create function**.
![Lambda Create Connection](/images/6-2/0001.png)
![Lambda Create Connection](/images/6-2/0002.png)
2. **Function name**: `WebSocketConnectionHandler`. Runtime: `Python 3.12`.
![Lambda Create Connection](/images/6-2/0003.png)
3. Click **Create function**.
![Lambda Create Connection](/images/6-2/0004.png)
4. In the Code section, paste the connection handling code. You can find this source code in the `infra/modules/simple_websocket.py` file. Click **Deploy**.

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
5. Grant Permissions: Go to the **Configuration** tab -> **Permissions** to grant the Lambda permission to operate on the `simple-websocket-connections` table. Click the Role link (usually looks like `WebSocketConnectionHandler-role-xxxx`, where `xxxx` are random AWS characters) to open the IAM Role management interface.
![Lambda Create Connection](/images/6-2/0006.png)

6. On the Permissions tab, click the Add permissions button -> select Create inline policy. Select the JSON tab and paste the following code (remember to change the table ARN as appropriate), then click **Next**.
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
7. Name the policy `LambdaWebSocketPolicy` and click **Create policy**.
![Lambda Create Connection](/images/6-2/0009.png)
