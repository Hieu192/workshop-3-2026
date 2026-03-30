---
title : "Cấu hình Real-time Updates với WebSocket (API Gateway + Lambda)"
date :  2025
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Tổng quan phần này

Hệ thống của chúng ta xử lý tin nhắn trong hàng đợi. Để người dùng thấy được trạng thái thay đổi ngay lập tức (Real-time), chúng ta cần thiết lập luồng kết nối WebSocket.

Các bước thực hiện:
- Tạo bảng lưu danh sách kết nối (Connections Table).
- Tạo Lambda Function quản lý việc đóng/mở kết nối.
- Thiết lập API Gateway WebSocket.
- Tạo Lambda Stream Processor để bắt sự kiện từ DB và phát sóng tới người dùng.

![WebSocket Flow Overview](/images/6/0001.png)
