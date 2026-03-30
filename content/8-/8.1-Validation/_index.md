---
title : "Validate the Solution"
date :  2025
weight : 1
chapter : false
pre : " <b> 8.1. </b> "
---

#### Validation Procedures

This section provides comprehensive testing procedures to validate the priority-based message processing system.

---

#### 1. Automated testing script

After you have completed the preceding steps, you can initiate a comprehensive testing script to validate priority processing and delay behavior:

```bash
#!/bin/bash
curl -X POST "$API_URL/api/items" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "High Priority Task",
    "priority": "High",
    "delay": 10
  }'
```

---

#### 2. Validation through the web interface

The following screenshot of the UI illustrates how the queueing mechanism can work with the real-time updates using WebSockets.

![Validation through Web interface](/images/8/monitor.png)

The web interface provides validation of the priority-based message processing system. Access the Amazon CloudFront URL to view the following information:
- Real-time message processing with live status updates.
- Queue statistics showing message distribution by priority.
- Processing timeline demonstrating priority bypass behavior.
- WebSocket connection status indicating real-time connectivity.
