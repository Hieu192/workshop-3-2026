---
title : "Deployment Script deploy.sh"
date :  2025
weight : 2 
chapter : false
pre : " <b> 8.2 </b> "
---

### Automated Deployment Script

The `deploy.sh` file in the project performs a "single command" sequence of actions:

1. **Environment Check:** Automatically verifies AWS CLI, account, and deployment region.
2. **Build & Push:** Executes `mvn clean package`, builds the Docker image from the JAR file, and pushes it to the ECR repository.
3. **Infrastructure Deployment:** Runs `cdk deploy --all` to build the VPC network and enable MQ, App Runner, and WebSocket.
4. **Frontend Synchronization:** Automatically retrieves the latest API and WebSocket URLs, populates the React source code, builds the Frontend, and deploys it directly to CloudFront via S3.

**Result:** Instead of taking hours and potentially making errors, you **only need to type one command: `./deploy.sh`**. Wait, and the entire Enterprise system will automatically appear.

---
*Note: Learning manual configuration (Console) helps you understand the fundamentals, while automation using code (IaC) is the standard approach for modern projects.*
