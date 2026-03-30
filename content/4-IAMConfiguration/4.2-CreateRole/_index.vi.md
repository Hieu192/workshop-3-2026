---
title : "Tạo Role cho App Runner"
date :  2025
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---

#### Tạo Instance Role

Sau khi tạo Policy, chúng ta cần gán nó vào một Role để App Runner có thể mượn quyền khi khởi chạy Backend.

1. Ở menu IAM bên trái, chọn **Roles** -> **Create role**.
![IAM Role Create](/images/4-2/0001.png)
2. **Trusted entity type**: Chọn **Custom trust policy**. Dán đoạn mã sau vào:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "build.apprunner.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```
![IAM Role Create](/images/4-2/0002.png)

3. Ô Add permissions, tìm kiếm policy `AppRunnerPriorityPolicy` vừa tạo ở bước 4.1, tích chọn nó. Nhấn **Next**.
![IAM Role Create](/images/4-2/0003.png)

4. Ở **Name, Review, and Create** đặt tên Role là `AppRunnerPriorityInstanceRole`.
![IAM Role Create](/images/4-2/0004.png)
5. Nhấn **Create role**.
![IAM Role Create](/images/4-2/0005.png)
![IAM Role Create](/images/4-2/0006.png)
