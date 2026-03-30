---
title : "Tạo Bucket S3 Nội bộ"
date :  2025
weight : 1 
chapter : false
pre : " <b> 7.1 </b> "
---

#### Tạo Bucket S3 cho Frontend

Dự án này hướng tới tiêu chuẩn bảo mật Enterprise. S3 Bucket của chúng ta sẽ không Public, mà chỉ cho phép duy nhất dịch vụ CloudFront truy cập.

1. Truy cập dịch vụ **S3** -> **Create bucket**.
![S3 Private Bucket](/images/7-1/0001.png)
![S3 Private Bucket](/images/7-1/0002.png)
2. **Bucket name**: `priority-frontend-bucket-2025` (Lưu ý: Bạn chọn tên bất kỳ phù hợp, không được trùng lặp trên toàn cầu).
![S3 Private Bucket](/images/7-1/0003.png)
3. Đảm bảo ô **Block all public access** được chọn đầy đủ.
![S3 Private Bucket](/images/7-1/0004.png)
4. Bấm **Create bucket**.

![S3 Private Bucket](/images/7-1/0005.png)

