---
title : "Solution Validation"
date :  2025
weight : 1
chapter : false
pre : " <b> 8.1. </b> "
---

#### Solution Validation Process

This section provides comprehensive testing steps to verify the priority-based message processing system.

---

#### 1. Automated Testing Script

After completing the deployment steps, you can execute a comprehensive test script to check priority and delay processing behaviors:

```bash
#!/bin/bash
# Simple API Test Script - Hardcoded for immediate use
# Usage: ./test-api.sh [delay] [title] [priority]

# --- HARDCODED CONFIGURATION ---
API_URL="" -> replace with your App Runner link
# -------------------------------

# Parameters with defaults
DELAY=${1:-5}
TITLE=${2:-"Simple Test Task"}
MESSAGE="${DELAY}s delay processing task"
PRIORITY=${3:-"Medium"}
STATUS="Pending"

echo "🧪 Testing API at: $API_URL"
echo "📝 Creating item..."
echo "   Title:    $TITLE"
echo "   Message:  $MESSAGE"
echo "   Priority: $PRIORITY"
echo "   Delay:    ${DELAY}s"
echo ""

# Execute POST request
RESPONSE=$(curl -X POST "$API_URL/api/items" \
  -H "Content-Type: application/json" \
  -d "{
    \"title\": \"$TITLE\",
    \"message\": \"$MESSAGE\",
    \"priority\": \"$PRIORITY\",
    \"status\": \"$STATUS\",
    \"delay\": $DELAY
  }" \
  --silent)

# Check if response looks like success (should contain an ID)
if [[ $RESPONSE == *"id"* ]]; then
    echo "✅ Test completed successfully!"
    echo "📦 Response: $RESPONSE"
else
    echo "❌ Test failed with response:"
    echo "$RESPONSE"
fi

```

Create a `.sh` file with the source code above (after replacing `$API_URL` with your App Runner URL) and execute it to see messages being queued.

Run with: 

```bash
./test-api.sh 10 "High Priority Task" "High"
```

---

#### 2. Validation through Web Interface

The image below illustrates how the queue mechanism works in tandem with real-time WebSocket updates:

![Web UI Interface](/images/8-1/0001.jpeg)

The web interface allows you to validate the system according to the following criteria:
- **Live status updates**: Messages change from `QUEUED` to `COMPLETED` as soon as they are processed via WebSocket.
- **Queue statistics**: View message distribution across priority levels (High/Medium/Low).
- **Processing Timeline**: Observe the "bypass" behavior where High Priority messages skip the delay queue.
- **WebSocket Status**: Displays an active connection to receive messages from DynamoDB Streams.

Access the CloudFront URL created in the previous step to open this interface. If the system is working correctly, you will see "High Priority" messages processed before lower priority messages even if they have the same delay.
