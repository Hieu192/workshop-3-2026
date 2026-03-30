---
title : "Update Bucket Policy and Upload Frontend"
date :  2025
weight : 4 
chapter : false
pre : " <b> 7.4 </b> "
---

#### Permissions Setup and Source Code Upload

1. Once CloudFront finishes creating the distribution, copy the **Bucket Policy**.
   - From CloudFront, access Origins, click on your Origin ID, and then click **Edit**.
![CloudFront Origin Edit](/images/7-3/0001.png)
![CloudFront Origin Policy Copy](/images/7-3/0002.png)

2. Go back to the **S3** service, enter your bucket, and select the **Permissions** tab -> **Bucket Policy** -> **Edit**. Paste the copied JSON in.
   - This step allows CloudFront OAC to retrieve files from your bucket.
![S3 Bucket Policy Update](/images/7-3/0003.png)
![S3 Bucket Policy Save](/images/7-3/0004.png)

3. **Download and Configure the source code**:
   - First, download the Frontend source code zip file here: [spa-app.zip](/spa-app.zip)
   - After downloading, extract it on your computer.
   - On your computer, open `spa-app/src/App.js` in your IDE from the extracted folder. Update the parameters:
     - `IdentityPoolId`, `ALLOWED_API_BASE`, `ALLOWED_WS_BASE`.
![Frontend Configuration](/images/7-3/0005.png)

   - Run the following commands:
```bash
   cd spa-app
   npm install
   npm run build
```
![Frontend Build](/images/7-3/0006.png)

5. Upload everything from the `build/` folder to the `priority-frontend-bucket-2025` S3 Bucket.

```bash
aws s3 sync build/ s3://priority-frontend-bucket-2025 --delete
```
![S3 Sync](/images/7-3/0007.png)
   - Verify on the S3 Console.
![S3 Verification](/images/7-3/0008.png)
