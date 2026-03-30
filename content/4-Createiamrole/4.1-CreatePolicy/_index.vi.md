---
title : "Tạo Policy (Chính sách quyền)"
date :  2025
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

#### Tạo Policy cho App Runner

Dịch vụ App Runner (Backend) cần có các quyền truy cập vào bảng DynamoDB và giải mã mật khẩu từ Secrets Manager.

1. Truy cập dịch vụ **IAM** -> **Policies** -> **Create policy**.
![IAM Policy Create](/images/4-1/0001.png)
![IAM Policy Create](/images/4-1/0002.png)
2. Chọn tab **JSON** và dán đoạn mã sau vào (cấp quyền vào bảng DB và lấy Secret):
   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "dynamodb:PutItem",
                   "dynamodb:GetItem",
                   "dynamodb:UpdateItem",
                   "dynamodb:DeleteItem",
                   "dynamodb:Scan"
               ],
               "Resource": "*"
           },
           {
               "Effect": "Allow",
               "Action": "secretsmanager:GetSecretValue",
               "Resource": "*"
           }
       ]
   }
   ```
![Secrets Manager Logo](/images/4-1/0003.png)
3. Nhấn **Next**, đặt tên Policy là `AppRunnerPriorityPolicy` và nhấn **Create policy**.

![IAM Policy Create](/images/4-1/0004.png)
