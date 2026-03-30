---
title : "Manual Cleanup (Console)"
date :  2025
weight : 1 
chapter : false
pre : " <b> 10.1 </b> "
---

### Clean Up Resources on the Console

To avoid unwanted costs, make sure to delete these resources after completing the lab:

1. **AWS App Runner**: Delete the `priority-backend-api` service.
2. **Amazon MQ (Broker)**: Delete the `PriorityMessageBroker` broker.
3. **S3 Bucket**: Empty all contents and delete the `priority-frontend-bucket-2025` S3 bucket.
4. **CloudFront**: Select the Distribution, click **Disable**, and then click **Delete**.
5. **DynamoDB**: Delete the `PriorityItemsTable` and `simple-websocket-connections` tables.
6. **Secrets Manager**: Select the `MessagingStack-MessagingMqPassword` secret and click **Delete secret**.
7. **ECR Repository**: Delete the `priority-spring-app` repository.
