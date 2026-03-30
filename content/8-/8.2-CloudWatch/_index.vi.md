---
title : "Giám sát với CloudWatch"
date :  2025
weight : 2
chapter : false
pre : " <b> 8.2. </b> "
---

#### Dashboard và Dashboard Cảnh báo Amazon CloudWatch

AWS khuyến nghị tạo Amazon CloudWatch dashboards để theo dõi hiệu suất của hệ thống xử lý tin nhắn ưu tiên trên nhiều khía cạnh khác nhau. 

**Giám sát theo Mức ưu tiên (Monitoring by Priority Levels):**
Bạn có thể theo dõi việc xử lý tin nhắn theo các mức độ ưu tiên để đảm bảo rằng các tin nhắn có độ ưu tiên cao (High Priority) luôn được xử lý trước. Điều này cũng giúp xác định bất kỳ "điểm nghẽn" (bottlenecks) nào trong logic định tuyến ưu tiên của bạn.

![CloudWatch Dashboard Mẫu](/images/8-2/0001.png)

*Hình ảnh trên mô tả một ví dụ dashboard theo dõi số lượng tin nhắn xử lý thành công theo từng cấp độ ưu tiên.*

**Xác định tải hệ thống và Latency:**
Theo dõi độ sâu của hàng đợi (Queue Depth) và thời gian xử lý (Processing Times) để hiểu rõ tải trọng của hệ thống và các mô hình độ trễ. Điều này giúp tối ưu hóa việc phân bổ tài nguyên và xác định thời điểm cần thực hiện mở rộng (Scaling).

![Theo dõi DynamoDB Performance](/images/8-2/0002.png)

**Theo dõi hiệu suất DynamoDB:**
Quan sát các chỉ số hiệu suất của DynamoDB bao gồm tiêu thụ Read/Write Capacity, các sự kiện throttling (bị hạn chế do quá tải) và độ trễ để đảm bảo lớp cơ sở dữ liệu duy trì hiệu suất tối ưu dưới các mức tải thay đổi.

**Bổ sung chỉ số tùy chỉnh (Custom Metrics):**
Ngoài ra, hãy triển khai các chỉ số tùy chỉnh dành riêng cho ứng dụng như tỷ lệ xử lý tin nhắn thành công, số lượng lần thử lại (retry counts) và các KPI đặc thù của doanh nghiệp để có cái nhìn sâu sắc hơn về hành vi của ứng dụng và đưa ra quyết định dựa trên dữ liệu để cải tiến liên tục.
