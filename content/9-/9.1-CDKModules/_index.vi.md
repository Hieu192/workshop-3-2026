---
title : "Hiểu về CDK Modules"
date :  2025
weight : 1 
chapter : false
pre : " <b> 8.1 </b> "
---

### Hiểu về AWS CDK (Infrastructure as Code)

Tất cả 7 phần làm việc cực nhọc phía trước với hàng chục cú click chuột có thể được thực hiện hoàn toàn tự động bằng mã nguồn. AWS CDK cho phép chúng ta thiết kế hạ tầng bằng các file Python. Tại thư mục `/infra/modules/` bạn sẽ thấy:
- **`simple_websocket.py`**: Định nghĩa ApiGatewayV2 và 2 hàm Lambda.
- **`spa_frontend.py`**: Định nghĩa CloudFront distribution và S3 OAC.
- **`messaging.py`**: Định nghĩa Amazon MQ và các tham số kỹ thuật (ActiveMQ).
- **`app_runner.py`**: Định nghĩa AWS App Runner service liên kết với ECR image.

Dùng lệnh `cdk deploy --all` để ra lệnh cho AWS CloudFormation xây dựng mạng lưới VPC và hạ tầng một cách đồng bộ.

