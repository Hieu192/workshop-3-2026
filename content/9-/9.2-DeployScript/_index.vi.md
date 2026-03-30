---
title : "Kịch bản triển khai deploy.sh"
date :  2025
weight : 2 
chapter : false
pre : " <b> 8.2 </b> "
---

### Kịch bản Triển khai Tự động

File `deploy.sh` trong dự án thực hiện chuỗi hành động "một lệnh duy nhất":

1. **Check Môi trường:** Tự động kiểm tra AWS CLI, tài khoản và vùng triển khai.
2. **Build & Push:** Tự chạy `mvn clean package`, build Docker image từ file JAR và push lên kho ECR.
3. **Triển khai Hạ tầng:** Chạy lệnh `cdk deploy --all` để xây dựng mạng lưới VPC, bật MQ, App Runner và WebSocket.
4. **Đồng bộ Frontend:** Gắp các đầu API URL và WebSocket URL mới nhất điền vào mã nguồn React, build Frontend rồi đẩy trực tiếp lên CloudFront qua S3.

**Kết quả:** Thay vì mất hàng giờ và dễ sai sót một chữ nào đó. Thực tế, bạn **chỉ cần gõ 1 lệnh `./deploy.sh`**, ngồi chờ và toàn bộ hệ thống Enterprise sẽ tự động xuất hiện.

---
*Ghi chú: Việc học cách cấu hình tay (Console) giúp bạn hiểu bản chất, nhưng tự động hóa bằng code (IaC) mới là cách làm chuẩn của các dự án hiện đại.*
