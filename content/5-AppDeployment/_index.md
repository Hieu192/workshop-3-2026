---
title : "Deploy Spring Boot Application to AWS (ECR + App Runner)"
date :  2025
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

### Section Overview

We will deploy our Backend source code to the cloud using a Container architecture. This is split into 2 steps:
- Package the Image and push it to Amazon ECR.
- Run the application on AWS App Runner - a Serverless Container service.

Main topics in this section:
- Build and Push the Docker Image.
- Launch the Backend API and configure environment variables.

![App Runner Overview](/images/5/0001.png)
