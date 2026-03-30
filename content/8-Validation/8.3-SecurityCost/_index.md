---
title : "Security and Cost"
date :  2025
weight : 3
chapter : false
pre : " <b> 8.3. </b> "
---

#### Security Considerations

AWS recommends implementing comprehensive security measures to safeguard your message processing system. 

- **IAM Policies**: Start by implementing least privilege IAM policies that grant only the minimum permissions required for each component to function, making sure services like App Runner can only access the specific DynamoDB tables and Amazon MQ queues they need. 
- **Network Architecture**: Configure your network architecture using a virtual private cloud (VPC) with private subnets for Amazon MQ, isolating your message broker from direct internet access while maintaining connectivity through NAT gateways for necessary outbound connections.
- **Encryption**: Enable encryption at rest using AWS Key Management Service (AWS KMS) for DynamoDB tables and Amazon MQ data and enforce encryption in transit by configuring SSL/TLS connections for all service communications, particularly for ActiveMQ broker connections. 
- **Security Groups**: Finally, configure security groups with minimal access rules that explicitly define allowed traffic between components, restricting inbound connections to only the ports and protocols required for your application to function, such as port 61617 for ActiveMQ SSL connections from App Runner instances.

---

#### Cost Considerations

The following table contains cost estimates based on the US East (N. Virginia) Region. Actual costs might vary based on your Region, usage patterns, and pricing changes.

| Service | Small (1,000 msg/day) | Medium (10,000 msg/day) | Large (100,000 msg/day) |
| :--- | :--- | :--- | :--- |
| **Amazon DynamoDB** | $5–10 | $25–50 | $200–400 |
| **Amazon MQ** | $15 (t3.micro) | $30 (m5.large) | $120 (m5.xlarge) |
| **AWS App Runner** | $20–40 | $50–150 | $400–800 |
| **Amazon API Gateway WebSocket** | $3–5 | $10–25 | $50–100 |
| **Amazon CloudWatch Logs** | $5–10 | $10–20 | $30–50 |
| **Data Transfer** | $5 | $10-20 | $50-100 |
| **Total Estimated Cost** | **$53–95** | **$135–295** | **$850–1,570** |
