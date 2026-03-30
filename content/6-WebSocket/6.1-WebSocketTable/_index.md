---
title : "Create Connections Table"
date :  2025
weight : 1 
chapter : false
pre : " <b> 6.1 </b> "
---

#### Create the simple-websocket-connections Table

WebSocket needs to know "who is connected" to send messages.

1. Go to **DynamoDB** -> **Tables** -> **Create table**.
![WebSocket Table Create](/images/6-1/0001.png)
![WebSocket Table Create](/images/6-1/0002.png)
2. - **Table name**: `simple-websocket-connections`.
   - **Partition key**: `connectionId` (String).
![WebSocket Table Create](/images/6-1/0003.png)
3. Click **Create table**, and the result should look like the following:
![WebSocket Table Create](/images/6-1/0004.png)
