---
title : "Solution Overview"
date :  2025
weight : 1 
chapter : false
---

# Building a Priority-Based Message Processing System

#### Introduction
Welcome to this detailed workshop on building an intelligent message distribution and processing system on AWS. This is a classic challenge in Enterprise systems, where we need to ensure High Priority requests are handled first, while maintaining a Delay mechanism for less critical tasks to optimize resources.

#### System Architecture
The system consists of several core components:
- **Backend:** Spring Boot 3 running on **AWS App Runner**.
- **Messaging:** **Amazon MQ (ActiveMQ)** supporting the JMS Priority standard.
- **Database:** **DynamoDB** to store processing states.
- **Real-time:** **WebSocket API (Gateway)** + **Lambda** for immediate status updates on the interface.
- **Frontend:** React SPA distributed via **CloudFront** and **S3**.

![Architecture Overview](/images/00/0001.jpeg)

#### What Will You Learn?
1. How to configure Amazon MQ to support priority queues.
2. How to use Secrets Manager to manage sensitive information.
3. How to set up a Real-time flow using DynamoDB Streams and WebSocket.
4. How to deploy containerized applications to App Runner.
5. How to secure Frontend applications with CloudFront Origin Access Control (OAC).

> [!NOTE]
> This workshop provides two methods: Manual configuration on the Console (to understand the fundamentals) and Full Automation using Source Code (IaC).

Let's get started by setting up the database in the next step!
