---
title : "Understanding CDK Modules"
date :  2025
weight : 1 
chapter : false
pre : " <b> 8.1 </b> "
---

### Understanding AWS CDK (Infrastructure as Code)

All 7 previous sections of intensive work involving dozens of clicks can be fully automated using source code. AWS CDK allows us to design infrastructure using Python files. In the `/infra/modules/` directory, you will find:
- **`simple_websocket.py`**: Defines ApiGatewayV2 and 2 Lambda functions.
- **`spa_frontend.py`**: Defines the CloudFront distribution and S3 OAC.
- **`messaging.py`**: Defines Amazon MQ and technical parameters (ActiveMQ).
- **`app_runner.py`**: Defines the AWS App Runner service linked to the ECR image.

Use the `cdk deploy --all` command to instruct AWS CloudFormation to build the VPC network and infrastructure in a synchronized manner.
