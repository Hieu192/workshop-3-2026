---
title : "Configure Real-time Updates with WebSocket (API Gateway + Lambda)"
date :  2025
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Section Overview

Our system processes messages in a queue. To allow users to see status changes immediately (Real-time), we need to set up a WebSocket connection flow.

Steps to perform:
- Create a table to store connection IDs (Connections Table).
- Create a Lambda Function to manage opening/closing connections.
- Set up an API Gateway WebSocket.
- Create a Lambda Stream Processor to capture events from the DB and broadcast them to users.

![WebSocket Flow Overview](/images/6/0001.png)