---
title : "Kiểm tra giao diện Web"
date :  2025
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### Tổng quan phần này

Sau khi đã thiết lập xong luồng WebSocket và triển khai ứng dụng Frontend lên CloudFront, chúng ta sẽ bắt đầu kiểm nghiệm hệ thống xử lý tin nhắn ưu tiên. Phần này sẽ hướng dẫn bạn cách thực hiện các bài kiểm tra tự động và thủ công, đồng thời quan sát quá trình xử lý tin nhắn theo thời gian thực (Real-time).

**Các nội dung chính:**
1. **Thiết lập WebSocket và Real-time**: Recap các bước cấu hình API Gateway và Lambda Stream Processor.
2. **Triển khai ứng dụng React**: Đưa mã nguồn frontend lên S3 và phân phối toàn cầu qua CloudFront.
3. **Kiểm chứng giải pháp**: Thực hiện các bài test gửi tin nhắn với mức ưu tiên khác nhau (High/Low/Medium).
4. **Giám sát qua CloudWatch**: Theo dõi hiệu năng hệ thống qua dashboard và cảnh báo.
5. **Cân nhắc Bảo mật và Chi phí**: Các yếu tố cần lưu ý để vận hành hệ thống một cách tối ưu.


