---
title : "Lưu trữ Mật khẩu với AWS Secrets Manager"
date :  2025
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

### Tổng quan phần này

Theo tiêu chuẩn bảo mật của AWS, các hệ thống backend không nên để mật khẩu trực tiếp trong mã nguồn. Chúng ta sẽ lưu trữ mật khẩu Broker này vào **Secrets Manager**.

Các nội dung chính trong phần này:
- Tạo một Secret mới chứa thông tin đăng nhập của Amazon MQ.
- Đặt tên khớp với cấu hình của mã nguồn.

![Secrets Manager Logo](/images/3/00001.png)


#### Tạo Secret cho Broker

Để tránh việc phải ghi trực tiếp mật khẩu Broker vào mã nguồn (Hardcode), chúng ta sẽ cất mật khẩu vào **Secrets Manager**.

1. Tìm và truy cập dịch vụ **Secrets Manager**.
![Secrets Manager Logo](/images/3/0002.png)
2. Nhấn nút **Store a new secret**.
![Secrets Manager Logo](/images/3/0003.png)
3. Ở mục **Secret type**, chọn **Other type of secret**. Chọn sang tab **Plaintext** và nhập nội dung JSON chứa thông tin đăng nhập MQ:
   ```json
   {
     "username": "admin",
     "password": "MyP@ssw0rd2025!"
   }
   ```
![Secrets Manager Logo](/images/3/0004.png)
- Tiếp tục kéo xuống dưới cùng và chọn **Next**.
![Secrets Manager Logo](/images/3/0005.png)
5. Ở phần **Configure secret**:
   - Đặt tên Secret là: `MessagingStack-MessagingMqPassword`. (Tên này phải trùng khớp hoàn toàn với cấu hình @Value trong Spring Boot).
   - Description: `Password for Amazon MQ Broker`
![Secrets Manager Logo](/images/3/0006.png)
- Tiếp tục kéo xuống dưới cùng và chọn **Next**.
![Secrets Manager Logo](/images/3/0007.png)

6. Ở phần **Configure rotation**, chọn **Disable automatic rotation** (mặc định). Nhấn **Next**.
![Secrets Manager Logo](/images/3/0008.png)

7. Ở phần **Review**, kiểm tra lại thông tin và nhấn **Store**.
![Secrets Manager Logo](/images/3/0009.png)
![Secrets Manager Logo](/images/3/0010.png)

---
*Ghi chú: Việc quản trị mật khẩu tập trung thông qua Secrets Manager giúp chúng ta dễ dàng thay đổi mật khẩu định kỳ mà không phải build lại code.*