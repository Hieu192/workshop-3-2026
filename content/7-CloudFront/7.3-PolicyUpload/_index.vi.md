---
title : "Cập nhật Bucket Policy và Tải lên Frontend"
date :  2025
weight : 4 
chapter : false
pre : " <b> 7.4 </b> "
---

#### Thiết lập quyền và Tải lên mã nguồn

1. Sau khi CloudFront tạo xong, hãy copy đoạn **Bucket Policy** 
   - Từ CloudFront, truy cập vào Origins, nhấn vào Origin ID của bạn và nhấn **Edit**
![S3 Bucket Policy Update](/images/7-3/0001.png)
![S3 Bucket Policy Update](/images/7-3/0002.png)

2. Quay lại dịch vụ **S3**, vào bucket của bạn an chọn tab **Permissions** -> **Bucket Policy** -> **Edit**. Dán đoạn JSON vừa copy vào.
   - Bước này cho phép CloudFront OAC được lấy file trong bucket của bạn.
![S3 Bucket Policy Update](/images/7-3/0003.png)
![S3 Bucket Policy Update](/images/7-3/0004.png)
3. **Tải và Cấu hình mã nguồn**:
   - Trước tiên, hãy tải thư mục nén chứa mã nguồn Frontend tại đây: [spa-app.zip](/spa-app.zip)
   - Sau khi tải về, hãy giải nén ra máy tính của bạn.
   - Ở máy tính, mở `spa-app/src/App.js` từ thư mục giải nén đó bằng IDE. Cập nhật 3 tham số:
 IdentityPoolId, ALLOWED_API_BASE, ALLOWED_WS_BASE

![S3 Bucket Policy Update](/images/7-3/0005.png)
   - Chạy lệnh:
```bash
   cd spa-app
   npm install
   npm run build
```
![S3 Bucket Policy Update](/images/7-3/0006.png)

5. Tải toàn bộ nội dung trong thư mục `build/` lên S3 Bucket `priority-frontend-bucket-2025`.

```bash
aws s3 sync build/ s3://priority-frontend-bucket-2025 --delete
```
![S3 Bucket Policy Update](/images/7-3/0007.png)
   - Kiếm tra S3 trên console.
![S3 Bucket Policy Update](/images/7-3/0008.png)

