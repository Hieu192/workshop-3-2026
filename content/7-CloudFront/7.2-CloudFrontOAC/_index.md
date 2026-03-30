---
title : "Create CloudFront Distribution"
date :  2025
weight : 2 
chapter : false
pre : " <b> 7.2 </b> "
---

#### Create CloudFront

This is a security mechanism that allows S3 to "recognize" that requests are coming from CloudFront, helping to protect data in S3 from unauthorized access.

1. Access the **CloudFront** service and click **Create distribution**.
![CloudFront Setup](/images/7-2/0001.png)
![CloudFront Setup](/images/7-2/0002.png)
2. **Choose a plan**
   - Select the **Free** plan ($0/month) to utilize the features available within the free tier. Click **Next**.
![CloudFront Setup](/images/7-2/0003.png)
3. **Get started**
   - **Distribution name**: Give it a descriptive name, e.g., `priority-frontend-demo`.
   - **Description**: `CloudFront for Priority Demo Application`.
   - **Distribution type**: Keep as **Single website or app**.
   - Click **Next**.
![CloudFront Setup](/images/7-2/0004.png)
4. **Specify origin** (Origin configuration)
   - **Origin type**: Select **Amazon S3**.
   - **S3 origin**: Click in the box and select the S3 Bucket you created (`priority-frontend-bucket-2025...`).
   - **Origin path**: `index.html`
   - **Settings**: Ensure **Allow private S3 bucket access to CloudFront - Recommended** is selected. This option automatically sets up OAC for you.
   - Keep the **Recommended** options for Origin settings and Cache settings. Click **Next**.
![CloudFront Setup](/images/7-2/0005.png)
5. **Enable security**
   - The system will automatically include basic protection (WAF). You can keep the defaults and click **Next**.
![CloudFront Setup](/images/7-2/0006.png)
6. **Review and create**
   - Review all information. Ensure that **Grant CloudFront access to origin** is set to **Yes**.
   - Click **Create distribution**.
![CloudFront Setup](/images/7-2/0007.png)
![CloudFront Setup](/images/7-2/0008.png)

---
**Note after creation:**
The system will provide you with a **Distribution domain name** (e.g., `xxxx.cloudfront.net`). Save this URL to access the application in the final step.
