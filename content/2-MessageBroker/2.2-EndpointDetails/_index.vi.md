---
title : "Ghi lại Endpoint URL"
date :  2025
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

#### Lấy thông số Endpoint

Quá trình khởi tạo Broker có thể kéo dài tới 15-20 phút. Sau khi trạng thái là **Running**, hãy nhấn vào tên Broker của bạn.

1. Tìm mục **Endpoints**.
![Broker Endpoints](/images/2-2/0001.png)
2. Copy địa chỉ URL cho giao thức **OpenWire** (Giao thức sử dụng `ssl://...`). Ví dụ: `ssl://b-12345-1.mq.us-east-1.amazonaws.com:61617`.
![Broker Endpoints](/images/2-2/0002.png)
3. Giữ thông số này cẩn thận, đây là URL bạn sẽ cần điền vào biến môi trường của Spring Boot ở các phần sau.

4. Thêm security group. Thêm quy tắc mới để cho phép apprunner có thể truy cập được như sau:
    - Type: Custom TCP
    - Port Range: 61617
    - Source: Chọn 0.0.0.0/0 (Để cho phép App Runner từ Internet có thể gõ cửa).
    - Description: Allow App Runner to ActiveMQ
![Broker Endpoints](/images/2-2/0003.png)
![Broker Endpoints](/images/2-2/0004.png)
![Broker Endpoints](/images/2-2/0005.png)

