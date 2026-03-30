---
title : "Solution Validation"
date :  2025
weight : 1
chapter : false
pre : " <b> 8.1. </b> "
---

#### Solution Validation Procedures

This section provides comprehensive testing steps to verify the priority-based message processing system.

---

#### 1. Automated Testing Script

After completing the deployment steps, you can execute a comprehensive test script to check priority behavior and delay handling:

```bash
#!/bin/bash
# Example of sending a High Priority message with a specific delay
curl -X POST "$API_URL/api/items" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "High Priority Task",
    "priority": "High",
    "delay": 10
  }'
```

Create a `.sh` file with the source code above (after replacing `$API_URL` with your App Runner URL) and execute it to see messages being queued.

---

#### 2. Validation through Web Interface

The image below illustrates how the queuing mechanism works in parallel with real-time WebSocket updates:

![Web UI Interface](/images/8-1/0001.jpeg)

The web interface allows you to validate the system based on the following criteria:
- **Live Status Updates**: Messages change from `QUEUED` to `COMPLETED` as soon as they are processed via WebSocket.
- **Queue Statistics**: View message distribution across priority levels (High/Medium/Low).
- **Processing Timeline**: Observe "bypass" behavior where High Priority messages skip the delay queue.
- **WebSocket Status**: Displays active connections receiving messages from DynamoDB Streams.

Access the CloudFront URL created in the previous step to open this interface. If the system is working correctly, you should see "High Priority" messages processed before lower priority ones, even if they have the same delay value.
