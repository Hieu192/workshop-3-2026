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
