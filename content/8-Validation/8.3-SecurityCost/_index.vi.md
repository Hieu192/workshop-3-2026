---
title : "Bảo mật và Chi phí"
date :  2025
weight : 3
chapter : false
pre : " <b> 8.3. </b> "
---

#### Cân nhắc về Bảo mật (Security Considerations)

AWS khuyên bạn nên thực hiện các biện pháp bảo mật toàn diện để bảo vệ hệ thống xử lý tin nhắn của mình:

- **Nguyên tắc Quyền tối thiểu (Least Privilege)**: Áp dụng các chính sách IAM chỉ cấp các quyền tối thiểu cần thiết cho mỗi thành phần để hoạt động, đảm bảo các dịch vụ như App Runner chỉ có thể truy cập các bảng DynamoDB và hàng đợi Amazon MQ cụ thể mà họ cần.
- **VPC và Cách ly Mạng**: Cấu hình cấu trúc mạng của bạn bằng VPC với các subnet riêng tư cho Amazon MQ, cách ly backend khỏi việc truy cập trực tiếp từ Internet trong khi vẫn duy trì khả năng kết nối thông qua NAT Gateways cho các kết nối outbound cần thiết.
- **Mã hóa dữ liệu (Encryption)**: Bật mã hóa dữ liệu khi nghỉ (Encryption at rest) bằng **AWS KMS** cho các bảng DynamoDB và dữ liệu Amazon MQ. Đồng thời thực thi mã hóa khi truyền tải (Encryption in transit) bằng cách định cấu hình kết nối SSL/TLS cho tất cả các thông tin liên lạc dịch vụ, đặc biệt là đối với các kết nối Broker ActiveMQ.
- **Security Groups**: Thiết lập các quy tắc truy cập tối thiểu, chỉ cho phép luồng giao thông giữa các thành phần cần thiết cho sự vận hành của ứng dụng, ví dụ như cổng 61617 cho các kết nối SSL của ActiveMQ từ các thực thể App Runner.

---

#### Cân nhắc về Chi phí (Cost Considerations)

Bảng dưới đây chứa các ước tính chi phí dựa trên khu vực US East (N. Virginia). Chi phí thực tế có thể thay đổi tùy thuộc vào khu vực của bạn, mức sử dụng và các thay đổi về giá cả.

| Dịch vụ | Thấp (1,000 msg/ngày) | Trung bình (10,000 msg/ngày) | Cao (100,000 msg/ngày) |
| :--- | :--- | :--- | :--- |
| **Amazon DynamoDB** | $5–10 | $25–50 | $200–400 |
| **Amazon MQ** | $15 (t3.micro) | $30 (m5.large) | $120 (m5.xlarge) |
| **AWS App Runner** | $20–40 | $50–150 | $400–800 |
| **Amazon API Gateway WebSocket** | $3–5 | $10–25 | $50–100 |
| **Amazon CloudWatch Logs** | $5–10 | $10–20 | $30–50 |
| **Data Transfer** | $5 | $10-20 | $50-100 |
| **Tổng ước tính chi phí** | **$53–95** | **$135–295** | **$850–1,570** |
