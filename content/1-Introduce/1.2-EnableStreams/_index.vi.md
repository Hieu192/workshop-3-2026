---
title : "Bật DynamoDB Streams"
date :  2025
weight : 2 
chapter : false
pre : " <b> 1.2 </b> "
---

#### Bật DynamoDB Streams

Đây là cơ chế quan trọng: Mỗi khi một bản ghi trong DynamoDB thay đổi, một "sự kiện" sẽ được gửi ra ngoài, cho phép hệ thống đồng bộ dữ liệu Real-time.

1. Trong danh sách Tables, nhấn vào tên bảng `PriorityItemsTable` vừa tạo.
![DynamoDB Table](/images/1-2/0001.png)
2. Chuyển sang tab **Exports and streams**.
![DynamoDB Table](/images/1-2/0002.png)
3. Kéo xuống mục **DynamoDB stream details**, nhấn nút **Turn on**.
![DynamoDB Table](/images/1-2/0003.png)
4. Ở cửa sổ hiện ra chọn **New image** (để truyền tải toàn bộ dữ liệu mới nhất khi có sự thay đổi), sau đó nhấn **Turn on stream**.
![DynamoDB Table](/images/1-2/0004.png)
![DynamoDB Table](/images/1-2/0005.png)

---
*Ghi chú: Luồng DynamoDB này sau này sẽ được lắng nghe bởi một hàm Lambda để bắn thông báo qua WebSocket.*
