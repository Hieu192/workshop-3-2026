---
title : "Tạo Bảng (Table)"
date :  2025
weight : 1 
chapter : false
pre : " <b> 1.1 </b> "
---

#### Tạo Bảng DynamoDB

1. Đăng nhập vào **AWS Management Console**.
2. Trên thanh tìm kiếm ở trên cùng, gõ **DynamoDB** và chọn dịch vụ DynamoDB.
![DynamoDB Table](/images/1-1/0001.png)
3. Ở menu bên trái, chọn **Tables**, sau đó nhấn nút màu cam **Create table**.
![DynamoDB Table](/images/1-1/0002.png)
4. Tại phần **Table details**:
   - **Table name**: Nhập `PriorityItemsTable`
   - **Partition key**: Nhập `id` (đảm bảo kiểu dữ liệu là `String`)
![DynamoDB Table](/images/1-1/0003.png)
5. Tại phần **Table settings**, để mặc định là **Default settings**.
![DynamoDB Table](/images/1-1/0005.png)
6. Cuộn chuột xuống dưới cùng và chọn **Create table**. Bạn chờ khoảng 1-2 phút trạng thái bảng sẽ chuyển sang *Active*.

![DynamoDB Table](/images/1-1/0006.png)
