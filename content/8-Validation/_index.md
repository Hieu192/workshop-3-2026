---
title : "Validation with Web Interface"
date :  2025
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### This section Overview

After setting up the WebSocket stream and deploying the Frontend Application to CloudFront, we will begin validating the priority-based message processing system. This section provides detailed testing procedures (manual and automated) and explains how to monitor the real-time processing flow.

**Main topics:**
1. **Set up real-time updates**: Recap of API Gateway and Lambda Stream Processor configuration.
2. **Deploy React Frontend**: Build and upload the frontend to S3/CloudFront.
3. **Validate the Solution**: Send messages with varying priorities (High/Low/Medium).
4. **CloudWatch Monitoring**: Track performance with dashboards and alarms.
5. **Security and Cost Considerations**: Key operational factors for production.

![Amazon MQ Monitor Web UI](/images/8/monitor.png)

---

#### 1. Set up real-time updates
For this step, we implement WebSocket support for real-time status updates using AWS Lambda to process DynamoDB streams and send updates to connected clients using Amazon API Gateway WebSocket connections. You can find the code snippet for this in [this link](../6-WebSocket/).

#### 2. Deploy the React application to Amazon S3 and Amazon CloudFront
In this step, we create a frontend application to enable the WebSocket connection for seeing the messages getting updated in the DynamoDB and API Gateway WebSocket connections.
*Refer to the AWS CDK code for building the frontend in [this section](../7-CloudFront/).*

Proceed to the next page to start the **Validation Procedures**.
