---
title : "Security and Cost"
date :  2025
weight : 3
chapter : false
pre : " <b> 8.3. </b> "
---

#### Security Considerations

AWS recommends implementing comprehensive security measures to protect your message processing system:

- **Principle of Least Privilege**: Apply IAM policies that only grant the minimum necessary permissions for each component to operate. Ensure services like App Runner can only access specific DynamoDB tables and Amazon MQ queues as required.
- **VPC and Network Isolation**: Configure your network architecture using VPC with private subnets for Amazon MQ and isolate the backend from direct Internet access, while maintaining connectivity through NAT Gateways for necessary outbound connections.
- **Data Encryption**: Enable encryption at rest using **AWS KMS** for DynamoDB tables and Amazon MQ data. Also, enforce encryption in transit by configuring SSL/TLS connections for all service communications, especially for ActiveMQ Broker connections.
- **Security Groups**: Etablish minimum access rules, only allowing traffic between the components necessary for application operation, e.g., port 61617 for SSL connections from App Runner to ActiveMQ.

---

#### Cost Considerations

The table below provides cost estimates based on the US East (N. Virginia) region. Actual costs may vary depending on your region, usage, and pricing changes.

| Service | Low (1,000 msg/day) | Medium (10,000 msg/day) | High (100,000 msg/day) |
| :--- | :--- | :--- | :--- |
| **Amazon DynamoDB** | $5–10 | $25–50 | $200–400 |
| **Amazon MQ** | $15 (t3.micro) | $30 (m5.large) | $120 (m5.xlarge) |
| **AWS App Runner** | $20–40 | $50–150 | $400–800 |
| **Amazon API Gateway WebSocket** | $3–5 | $10–25 | $50–100 |
| **Amazon CloudWatch Logs** | $5–10 | $10–20 | $30–50 |
| **Data Transfer** | $5 | $10-20 | $50-100 |
| **Total Estimated Cost** | **$53–95** | **$135–295** | **$850–1,570** |
