---
title : "Đưa ứng dụng Spring Boot lên AWS (ECR + App Runner)"
date :  2025
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

### Tổng quan phần này

Chúng ta sẽ đưa mã nguồn Backend của mình lên đám mây thông qua kiến trúc Container. Phân tách thành 2 bước:
- Đóng gói Image và đẩy lên Amazon ECR.
- Chạy ứng dụng trên AWS App Runner - dịch vụ Container Serverless.

Các nội dung chính trong phần này:
- Build và Push Docker Image.
- Khởi chạy API Backend và thiết lập biến môi trường.

![App Runner Overview](/images/5/0001.png)
