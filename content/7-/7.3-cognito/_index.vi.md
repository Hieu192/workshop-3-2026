---
title : "Tạo Cognito Identity Pool"
date :  2025
weight : 3 
chapter : false
pre : " <b> 7.3 </b> "
---

#### Tổng quan về Cognito Identity Pool

Để Frontend (React SPA) có thể truy cập trực tiếp vào DynamoDB mà không cần thông qua Backend (để lấy dữ liệu thời gian thực), chúng ta sẽ sử dụng **Amazon Cognito Identity Pool**. Dịch vụ này cho phép cấp quyền AWS tạm thời cho người dùng cuối (ở đây là các "Guest" không cần đăng nhập).

![Cognito Architecture Logo](/images/7/0002.png)

#### Các bước thực hiện

1. Truy cập dịch vụ **Amazon Cognito** từ AWS Console.
![Lambda Stream Trigger](/images/7-3-cog/0001.png)

2. Chọn **Identity pools**. Nhấn nút **Create identity pool**.
![Lambda Stream Trigger](/images/7-3-cog/0002.png)
4. Configure trust policy:
   - Chọn **Guest access** (vì chúng ta muốn cho phép người dùng xem trang web mà không cần đăng nhập).
   - Nhấn **Next**.
![Lambda Stream Trigger](/images/7-3-cog/0003.png)
5. Configure permissions:
   - Tại mục **Guest access role**, chọn **Create a new IAM role**.
   - **Role name**: Nhập `PriorityAppGuestRole`.
   - Nhấn **Next**.
![Lambda Stream Trigger](/images/7-3-cog/0004.png)
6. Configure properties:
   - **Identity pool name**: Nhập `PriorityIdentityPool`.
   - Nhấn **Next**.
![Lambda Stream Trigger](/images/7-3-cog/0005.png)
7. Review and create:
   - Kiểm tra lại thông tin và nhấn **Create identity pool**.
![Lambda Stream Trigger](/images/7-3-cog/0006.png)

#### Cấp quyền cho IAM Role

Mặc định, Role `PriorityAppGuestRole` vừa tạo chưa có quyền thao tác với DynamoDB. Chúng ta cần bổ sung thêm:

1. Truy cập dịch vụ **IAM** -> **Roles**. Tìm và chọn Role có tên `PriorityAppGuestRole` (hoặc tên bạn đã đặt ở bước trên).
![Lambda Stream Trigger](/images/7-3-cog/0007.png)
2. Nhấn **Add permissions** -> **Create inline policy**.
![Lambda Stream Trigger](/images/7-3-cog/0008.png)
3. Chọn tab **JSON** và dán đoạn mã sau vào (Hãy đảm bảo tên bảng DynamoDB là `PriorityItemsTable`):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:Scan",
                "dynamodb:PutItem",
                "dynamodb:UpdateItem"
            ],
            "Resource": "*"
        }
    ]
}
```
![Lambda Stream Trigger](/images/7-3-cog/0009.png)

> Trong thực tế, bạn nên giới hạn Resource tới ARN cụ thể của bảng DynamoDB để đảm bảo bảo mật. Ở đây chúng ta dùng `*` cho mục đích demo nhanh.

4. Nhấn **Review policy**, đặt tên là `DynamoDBLimitedAccess` và nhấn **Create policy**.

#### Lưu lại Identity Pool ID

1. Quay lại trang chi tiết của Identity Pool `PriorityIdentityPool`.
2. Copy giá trị **Identity pool ID** (có dạng `ap-southeast-1:xxxxxxxx-xxxx-xxxx...`).
3. Bạn sẽ cần giá trị này ở bước tiếp theo để cấu hình trong mã nguồn Frontend.

