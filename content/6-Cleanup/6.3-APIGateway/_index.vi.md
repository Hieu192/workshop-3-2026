---
title : "Tạo API Gateway WebSocket"
date :  2025
weight : 3 
chapter : false
pre : " <b> 6.3 </b> "
---

#### Tạo API Gateway WebSocket

Dịch vụ này cung cấp một URL duy nhất để trình duyệt có thể giữ kết nối liên tục với hệ thống.

1. Truy cập **API Gateway** -> Chọn **Build** ở ô **WebSocket API**.
![API Gateway Setup](/images/6-3/0001.png)
![API Gateway Setup](/images/6-3/0002.png)
![API Gateway Setup](/images/6-3/0003.png)
2. - **API name**: `simple-websocket-api`.
   - **Route selection expression**: `request.body.action`.
   - Nhấn **Next**
![API Gateway Setup](/images/6-3/0004.png)

3. **Add routes**: Thêm 2 route `$connect` và `$disconnect`. Nhấn **Next**.
![API Gateway Setup](/images/6-3/0005.png)
4. **Attach integrations**: Cả 2 route này đều chọn Integration type là **Lambda** và chọn function `WebSocketConnectionHandler` vừa tạo ở 6.2. 
![API Gateway Setup](/images/6-3/0006.png)
5. Bấm **Next**, đặt **Stage name** là `prod`. Bấm **Next**.
![API Gateway Setup](/images/6-3/0007.png)

6. **Review and create**: kiểm tra hết lại và nhấn **Create and deploy**
![API Gateway Setup](/images/6-3/0008.png)
7. Cuối cùng, ghi lại URL WebSocket có dạng `wss://<api-id>.execute-api.<region>.amazonaws.com/prod`
![API Gateway Setup](/images/6-3/0009.png)
