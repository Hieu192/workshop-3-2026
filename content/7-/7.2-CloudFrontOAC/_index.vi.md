---
title : "Tạo CloudFront Distribution"
date :  2025
weight : 2 
chapter : false
pre : " <b> 7.2 </b> "
---

#### Tạo CloudFront

Đây là cơ chế bảo mật cho phép S3 "nhận diện" được rằng yêu cầu đang đến từ CloudFront, giúp chúng ta bảo vệ dữ liệu bên trong S3 không bị truy cập trái phép.
1. Truy cập dịch vụ **CloudFront** và nhấn **Create distribution**.
![CloudFront Setup](/images/7-2/0001.png)
![CloudFront Setup](/images/7-2/0002.png)
2. Choose a plan
   - Chọn gói **Free** ($0/month) để tận dụng các tính năng có sẵn trong hạn mức miễn phí. Nhấn **Next**.
![CloudFront Setup](/images/7-2/0003.png)
3. Get started
   - **Distribution name**: Đặt tên gợi nhớ, ví dụ: `priority-frontend-demo`.
   - **Description**: `CloudFront cho ứng dụng Priority Demo`.
   - **Distribution type**: Giữ nguyên **Single website or app**.
   - Nhấn **Next**.
![CloudFront Setup](/images/7-2/0004.png)
4. Specify origin (Cấu hình nguồn)
   - **Origin type**: Chọn **Amazon S3**.
   - **S3 origin**: Nhấn vào ô và chọn đúng Bucket S3 bạn đã tạo (`priority-frontend-bucket-2025...`).
   - **Origin path**: `index.html`
   - **Settings**: Đảm bảo đã tích chọn **Allow private S3 bucket access to CloudFront - Recommended**. Đây là tùy chọn tự động thiết lập OAC cho bạn.
   - Giữ nguyên các tùy chọn **Recommended** cho Origin settings và Cache settings. Nhấn **Next**.
![CloudFront Setup](/images/7-2/0005.png)
5. Enable security
   - Hệ thống sẽ tự động bao gồm các bảo vệ bảo bản (WAF). Bạn có thể giữ nguyên mặc định và nhấn **Next**.
![CloudFront Setup](/images/7-2/0006.png)
6. Review and create
   - Kiểm tra lại toàn bộ thông tin. Hãy đảm bảo mục **Grant CloudFront access to origin** là **Yes**.
   - Nhấn **Create distribution**.
![CloudFront Setup](/images/7-2/0007.png)
![CloudFront Setup](/images/7-2/0008.png)
---
**Lưu ý sau khi tạo:**
Hệ thống sẽ cung cấp cho bạn một **Distribution domain name** (có dạng `xxxx.cloudfront.net`). Bạn hãy lưu lại URL này để truy cập ứng dụng ở bước cuối cùng.
