---
title : "Tổng quan giải pháp"
date :  2025
weight : 1 
chapter : false
---

# Xây dựng Hệ thống Xử lý Tin nhắn Ưu tiên (Priority-Based Message Processing)

#### Giới thiệu
Chào mừng bạn đến với bài thực hành chi tiết về việc xây dựng một hệ thống phân phối và xử lý tin nhắn thông minh trên AWS. Đây là một bài toán kinh điển trong các hệ thống Enterprise, nơi chúng ta cần đảm bảo các yêu cầu quan trọng (High Priority) được xử lý trước, đồng thời có cơ chế trì hoãn (Delay) cho các tác vụ ít quan trọng hơn để tối ưu tài nguyên.

#### Kiến trúc hệ thống
Hệ thống bao gồm các thành phần cốt lõi:
- **Backend:** Spring Boot 3 chạy trên **AWS App Runner**.
- **Messaging:** **Amazon MQ (ActiveMQ)** hỗ trợ chuẩn JMS Priority.
- **Database:** **DynamoDB** lưu trạng thái xử lý.
- **Real-time:** **WebSocket API (Gateway)** + **Lambda** cập nhật trạng thái ngay lập tức lên giao diện.
- **Frontend:** React SPA phân phối qua **CloudFront** và **S3**.

![Architecture Overview](/images/00/0001.jpeg)

#### Bạn sẽ học được gì?
1. Cách cấu hình Amazon MQ hỗ trợ hàng đợi ưu tiên.
2. Cách sử dụng Secrets Manager để quản lý thông tin bảo mật.
3. Cách thiết lập luồng Real-time thông qua DynamoDB Streams và WebSocket.
4. Cách triển khai ứng dụng container hóa lên App Runner.
5. Cách bảo mật ứng dụng Frontend với CloudFront Origin Access Control (OAC).

> [!NOTE]
> Bài thực hành này cung cấp cả hai phương pháp: Tự tay cấu hình trên Console (để hiểu bản chất) và Tự động hóa hoàn toàn bằng mã nguồn (IaC).

Hãy bắt đầu bằng việc thiết lập cơ sở dữ liệu ở bước tiếp theo!
