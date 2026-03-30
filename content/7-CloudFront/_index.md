---
title : "Global Distribution and Security with CloudFront"
date :  2025
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Section Overview

The web interface (Frontend) of the application will be stored and secured according to Enterprise standards. It should absolutely not be completely Public on S3 but will only allow single access via the CloudFront CDN distribution service.

Steps to perform:
- Create an S3 Private Bucket to contain the Frontend source code.
- Set up the CloudFront service with the **Origin Access Control (OAC)** mechanism.
- Update the S3 Policy to only accept requests from this CloudFront CDN.
- Configure the API Backend URL and build the React SPA.

![CloudFront Architecture Logo](/images/7/0001.png)