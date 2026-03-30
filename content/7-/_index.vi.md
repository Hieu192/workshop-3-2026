---
title : "Phân phối toàn cầu và Bảo mật với CloudFront"
date :  2025
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Tổng quan phần này

Giao diện web (Frontend) của ứng dụng sẽ được lưu trữ và bảo mật theo chuẩn Enterprise. Tuyệt đối không để Public hoàn toàn trên S3 mà sẽ chỉ cho phép truy cập duy nhất qua dịch vụ phân phối CloudFront CDN.

Các bước thực hiện:
- Tạo S3 Private Bucket để chứa mã nguồn Frontend.
- Thiết lập dịch vụ CloudFront với cơ chế **Origin Access Control (OAC)**.
- Cập nhật Policy của S3 để chỉ chấp nhận yêu cầu từ cái CloudFront CDN đó.
- Cấu hình API Backend URL và build React SPA.

![CloudFront Architecture Logo](/images/7/0001.png)
