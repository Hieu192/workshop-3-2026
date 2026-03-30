---
title : "Dọn dẹp tự động (Script & CDK)"
date :  2025
weight : 2 
chapter : false
pre : " <b> 10.2 </b> "
---

### Dọn dẹp tự động hoàn toàn (Khuyên dùng)

Nếu bạn đã triển khai ứng dụng bằng `deploy.sh`, kịch bản dọn dẹp `destroy.sh` sẽ là cách an toàn và triệt để nhất để xóa bỏ mọi tài nguyên mà không gặp lỗi "thùng rác không trống" (Bucket not empty) hoặc "kho lưu trữ có ảnh" (ECR contains images).

#### 1. Chạy kịch bản dọn dẹp
Tại thư mục gốc của dự án, hãy sử dụng Git Bash (trên Windows) và chạy lệnh:
```bash
bash destroy.sh
```

**Kịch bản này sẽ tự động thực hiện:**
- **Làm trống S3 Bucket**: Xóa mọi dữ liệu và version của Frontend trước khi xóa Bucket.
- **Xóa ECR Images**: Dọn dẹp các bản build Docker trong AWS ECR.
- **Xóa CloudFront OAC & WAF**: Xóa các cấu hình bảo mật đặc thù của CDN.
- **cdk destroy --all**: Xóa tất cả các CloudFormation Stack (VPC, MQ, App Runner...) theo đúng thứ tự phụ thuộc ngược.

#### 2. Dọn dẹp chỉ với CDK (Cách thay thế)
Nếu bạn chỉ muốn xóa các Stack hạ tầng mà không cần dọn dẹp sâu dữ liệu S3/ECR:
1. Di chuyển vào thư mục `/infra`.
2. Chạy lệnh: `cdk destroy --all`

---
🎉 **XIN CHÚC MỪNG BẠN ĐÃ HOÀN THÀNH TOÀN BỘ BÀI THỰC HÀNH XỬ LÝ TIN NHẮN ƯU TIÊN TRÊN AWS!**
