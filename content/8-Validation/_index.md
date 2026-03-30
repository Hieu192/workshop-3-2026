---
title : "Validation with Web Interface"
date :  2025
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### Section Overview

After completing the WebSocket flow setup and deploying the Frontend application to CloudFront, we will begin testing the priority-based message processing system. This section will guide you on how to perform automated and manual tests and observe the message processing in Real-time.

**Main Topics:**
1. **WebSocket and Real-time Setup**: Recap of API Gateway and Lambda Stream Processor configuration.
2. **React App Deployment**: Uploading frontend source code to S3 and global distribution via CloudFront.
3. **Solution Validation**: Performing tests by sending messages with different priority levels (High/Low/Medium).
4. **Monitoring via CloudWatch**: Tracking system performance through dashboards and alerts.
5. **Security and Cost Considerations**: Factors to consider for optimal system operation.

---

#### 1. Set up Real-time Updates
In this step, we have implemented WebSocket support to update message status instantly. Using AWS Lambda to process DynamoDB Streams and send updates to connected users via Amazon API Gateway WebSocket connection.
*You can view the detailed source code and full instructions [here](../6-WebSocket/)* (Link to WebSocket configuration section).

#### 2. Deploy React Web App to S3 and CloudFront
We've created a React app to enable the WebSocket connection, allowing us to see messages updated dynamically in DynamoDB and API Gateway WebSocket notifications.
*Refer to detailed steps [here](../7-CloudFront/) (Link to CloudFront configuration section).*
