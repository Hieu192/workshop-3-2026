---
title : "Tự động hóa với Mã nguồn (Infra & Deploy.sh)"
date :  2025
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Tổng quan phần này

Tất cả các phần làm việc cực nhọc ở trên với hàng chục bước trên AWS Console có thể được thay thế hoàn toàn bởi **mã nguồn tự động hóa**. Đây là lý do cốt lõi của việc quản trị hạ tầng hiện đại.

Các nội dung chính trong phần này:
- Tìm hiểu về các module AWS CDK bằng Python ứng dụng trong dự án.
- Cách kịch bản `deploy.sh` tự động hóa build Docker, push ECR, deploy CDK/CloudFormation và đồng bộ Frontend.

Tải infra và file deploy, destroy tại đây (áp dụng cho windows): [Auto.zip](/Auto.zip)

Tải infra và file deploy, destroy tại đây (áp dụng cho linux): [Auto-linux.zip](/Auto-linux.zip)

