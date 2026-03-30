---
title : "Dọn dẹp Thủ công (Console)"
date :  2025
weight : 1 
chapter : false
pre : " <b> 10.1 </b> "
---

### Dọn dẹp tài nguyên trên Console

Để tránh phát sinh chi phí không mong muốn, hãy chắc chắn xóa các tài nguyên sau khi học xong bài lab này:

1. **AWS App Runner**: Xóa Service `priority-backend-api`.
2. **Amazon MQ (Broker)**: Xóa Broker `PriorityMessageBroker`.
3. **S3 Bucket**: Xóa sạch nội dung (Empty) và xóa cái S3 bucket `priority-frontend-bucket-2025`.
4. **CloudFront**: Chọn Distribution, bấm **Disable**, sau đó nhấn **Delete**.
5. **DynamoDB**: Xóa các bảng `PriorityItemsTable` và `simple-websocket-connections`.
6. **Secrets Manager**: Chọn Secret `MessagingStack-MessagingMqPassword`, bấm **Delete secret**.
7. **ECR Repository**: Xóa repository `priority-spring-app`.

