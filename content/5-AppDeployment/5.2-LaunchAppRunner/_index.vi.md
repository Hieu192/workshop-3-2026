---
title : "Khởi chạy AWS App Runner"
date :  2025
weight : 2 
chapter : false
pre : " <b> 5.2 </b> "
---

#### Khởi chạy AWS App Runner

1. Tìm và truy cập dịch vụ **AWS App Runner**.
![App Runner Creation](/images/5-2/0001.png)
2. Chọn **Create an App Runner service**.
![App Runner Creation](/images/5-2/0002.png)
3. **Source**: Chọn **Container registry** -> **Amazon ECR**.
   - Browse và chọn image `priority-spring-app:latest` bạn vừa đẩy lên.
![App Runner Creation](/images/5-2/0003.png)
![App Runner Creation](/images/5-2/0004.png)
4. Mục **Deployment trigger**, chọn **Manual**. Mục **ECR access role** chọn **Create new service  role**. Nhấn **Next**.
![App Runner Creation](/images/5-2/0005.png)
5. **Configure service**:
   - **Service name**: `priority-backend-api`
   - **Port**: `8080`
   - Kéo xuống mục **Environment variables**, thêm các biến sau:
     - `DYNAMODB_TABLE_NAME` = `PriorityItemsTable`
     - `MQ_BROKER_URL` = URL OpenWire `ssl://...` lấy ở **Phần 2.2**.
     - `AWS_REGION` = Region hiện tại của bạn (VD: `us-east-1`).
     - `MQ_USERNAME_SECRET_NAME` = `MessagingStack-MessagingMqPassword`
![App Runner Creation](/images/5-2/0006.png)
   - Kéo xuống mục **Security**, Ở phần **Instance role**, hãy chọn role `AppRunnerPriorityInstanceRole` đã tạo ở Phần 4.2.
![App Runner Creation](/images/5-2/0007.png)

   - Nhấn **Next**
![App Runner Creation](/images/5-2/0008.png)
6. Review lại mọi thứ và bấm **Create & deploy**.

![App Runner Creation](/images/5-2/0009.png)
![App Runner Creation](/images/5-2/0010.png)


