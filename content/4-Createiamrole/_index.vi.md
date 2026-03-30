---
title : "Cấu hình Quyền (IAM Role) cho Ứng dụng"
date :  2025
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

#### Tổng quan phần này

Backend của chúng ta (App Runner) cần quyền để đọc DynamoDB và giải mã mật khẩu từ Secrets Manager. Chúng ta sẽ làm điều này thông qua cơ chế Role và Policy.

Các nội dung chính trong phần này:
- Tạo Chính sách quyền (Policy JSON) chứa quyền đọc DB và Secrets.
- Tạo Role cho App Runner và gán chính sách đó vào.

![IAM Overview](/images/4/0001.png)
