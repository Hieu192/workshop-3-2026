---
title : "Khởi tạo Broker"
date :  2025
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

#### Khởi tạo Broker Amazon MQ

1. Tìm kiếm và truy cập dịch vụ **Amazon MQ** trên Console.
![Amazon MQ Setup](/images/2-1/0001.png)
2. Chọn **Create broker**.
![Amazon MQ Setup](/images/2-1/0002.png)
3. Ở bước **Select broker engine**, chọn **Apache ActiveMQ** và nhấn **Next**.
![Amazon MQ Setup](/images/2-1/0003.png)
4. Ở bước **Select deployment and storage**, chọn **Single-instance broker** (để tiết kiệm chi phí cho lab) và nhấn **Next**.
![Amazon MQ Setup](/images/2-1/0004.png)

5. Tại phần **Configure settings**:
- **Broker name**: Nhập `PriorityMessageBroker`
- **Broker instance type**: Chọn `mq.t3.micro`
- **ActiveMQ Web Console access**: Chuyển sang **Yes**
- **Username**: Nhập `admin`
- **Password**: `MyP@ssw0rd2025!` (Lưu ý: Bạn nên chọn mật khẩu mạnh hơn).
![Amazon MQ Setup](/images/2-1/0005.png)
- Tiếp theo kéo xuống dưới cùng và chọn **Next**.
![Amazon MQ Setup](/images/2-1/0006.png)

6. Tại phần **Review and create**, kiểm tra lại và nhấn **Create broker**.
![Amazon MQ Setup](/images/2-1/0007.png)
![Amazon MQ Setup](/images/2-1/0008.png)

7. Sau khi tạo xong, bạn chờ khoảng 15-20 phút để Broker chuyển sang trạng thái **Running**.
![Amazon MQ Setup](/images/2-1/0009.png)

