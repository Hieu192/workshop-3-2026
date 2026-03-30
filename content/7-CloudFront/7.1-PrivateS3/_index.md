---
title : "Create Private S3 Bucket"
date :  2025
weight : 1 
chapter : false
pre : " <b> 7.1 </b> "
---

#### Create S3 Bucket for Frontend

This project aims for Enterprise security standards. Our S3 Bucket will not be public; instead, it will only allow access from the CloudFront service.

1. Access the **S3** service -> **Create bucket**.
![S3 Private Bucket](/images/7-1/0001.png)
![S3 Private Bucket](/images/7-1/0002.png)
2. **Bucket name**: `priority-frontend-bucket-2025` (Note: Choose any suitable name; it must be globally unique).
![S3 Private Bucket](/images/7-1/0003.png)
3. Ensure the **Block all public access** checkbox is fully selected.
![S3 Private Bucket](/images/7-1/0004.png)
4. Click **Create bucket**.

![S3 Private Bucket](/images/7-1/0005.png)
