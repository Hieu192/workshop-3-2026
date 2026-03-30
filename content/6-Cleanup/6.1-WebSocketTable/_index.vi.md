---
title : "Tạo bảng connections"
date :  2025
weight : 1 
chapter : false
pre : " <b> 6.1 </b> "
---

#### Tạo bảng simple-websocket-connections

WebSocket cần biết "ai đang kết nối" để gửi tin nhắn.

1. Vào **DynamoDB** -> **Tables** -> **Create table**.
![WebSocket Table Create](/images/6-1/0001.png)
![WebSocket Table Create](/images/6-1/0002.png)
2. - **Table name**: `simple-websocket-connections`.
   - **Partition key**: `connectionId` (String).
![WebSocket Table Create](/images/6-1/0003.png)
3. Nhấn **Create table** và kết quả như dưới:
![WebSocket Table Create](/images/6-1/0004.png)


