---
title : "Launch AWS App Runner"
date :  2025
weight : 2 
chapter : false
pre : " <b> 5.2 </b> "
---

#### Launch AWS App Runner

1. Search for and access the **AWS App Runner** service.
![App Runner Creation](/images/5-2/0001.png)
2. Select **Create an App Runner service**.
![App Runner Creation](/images/5-2/0002.png)
3. **Source**: Select **Container registry** -> **Amazon ECR**.
   - Browse and select the `priority-spring-app:latest` image you just pushed.
![App Runner Creation](/images/5-2/0003.png)
![App Runner Creation](/images/5-2/0004.png)
4. In the **Deployment trigger** section, select **Manual**. In the **ECR access role** section, select **Create new service role**. Click **Next**.
![App Runner Creation](/images/5-2/0005.png)
5. **Configure service**:
   - **Service name**: `priority-backend-api`
   - **Port**: `8080`
   - Scroll down to the **Environment variables** section and add the following variables:
     - `DYNAMODB_TABLE_NAME` = `PriorityItemsTable`
     - `MQ_BROKER_URL` = OpenWire URL `ssl://...` retrieved in **Section 2.2**.
     - `AWS_REGION` = Your current region (e.g., `us-east-1`).
     - `MQ_USERNAME_SECRET_NAME` = `MessagingStack-MessagingMqPassword`
![App Runner Creation](/images/5-2/0006.png)
   - Scroll down to the **Security** section. In the **Instance role** part, select the `AppRunnerPriorityInstanceRole` created in Section 4.2.
![App Runner Creation](/images/5-2/0007.png)

   - Click **Next**.
![App Runner Creation](/images/5-2/0008.png)
6. Review everything and click **Create & deploy**.

![App Runner Creation](/images/5-2/0009.png)
![App Runner Creation](/images/5-2/0010.png)
