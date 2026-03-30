---
title : "Đưa mã nguồn lên ECR"
date :  2025
weight : 1 
chapter : false
pre : " <b> 5.1 </b> "
---

#### Đẩy mã nguồn lên Amazon ECR

1. **Tải và chuẩn bị mã nguồn Backend**:
   - Trước tiên, hãy tải thư mục nén mã nguồn Spring Boot tại đây: [spring-app.zip](/spring-app.zip)
   - Sau khi tải về, hãy giải nén ra máy tính của bạn.
   - Mở terminal tại thư mục `spring-app` vừa giải nén.
![ECR View Push Commands](/images/5-1/0001.png)

2. Build code thành file JAR:
```bash
mvn clean package -DskipTests
```
![ECR View Push Commands](/images/5-1/0002.png)

- Đây là file .jar sau khi build code.
![ECR View Push Commands](/images/5-1/0003.png)

3. Truy cập AWS Console, vào dịch vụ **Amazon ECR** -> **Repositories** -> **Create repository**.
   - **Repository name**: Nhập `priority-spring-app`.
   - Nhấn **Create repository**.
![ECR View Push Commands](/images/5-1/0004.png)
![ECR View Push Commands](/images/5-1/0005.png)
![ECR View Push Commands](/images/5-1/0006.png)

4. Mở repository vừa tạo, nhấn nút **View push commands** ở góc phải trên cùng. Lần lượt chạy 4 lệnh hiển thị trong cửa sổ đó trên terminal của bạn để đẩy image lên AWS.
![ECR View Push Commands](/images/5-1/0007.png)
![ECR View Push Commands](/images/5-1/0008.png)

- Bạn phải nhớ mở docker desktop trước khi chạy lệnh, không là lỗi như bên dưới
![ECR View Push Commands](/images/5-1/0009.png)
![ECR View Push Commands](/images/5-1/0010.png)
![ECR View Push Commands](/images/5-1/0011.png)

5. Sau khi chạy xong 4 lệnh, bạn kiểm tra lại trong ECR sẽ thấy kết quả như sau:
![ECR View Push Commands](/images/5-1/0012.png)



