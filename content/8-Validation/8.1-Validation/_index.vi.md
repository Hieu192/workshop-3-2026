---
title : "Kiểm chứng Giải pháp"
date :  2025
weight : 1
chapter : false
pre : " <b> 8.1. </b> "
---

#### Quy trình Kiểm chứng Giải pháp

Phần này cung cấp các bước kiểm thử toàn diện để xác minh hệ thống xử lý tin nhắn dựa trên mức độ ưu tiên.

---

#### 1. Kịch bản kiểm thử tự động (Automated testing script)

Sau khi hoàn tất các bước triển khai, bạn có thể thực hiện một kịch bản kiểm thử toàn diện để kiểm tra hành vi ưu tiên và xử lý trễ:

```bash
#!/bin/bash
# Simple API Test Script - Hardcoded for immediate use
# Usage: ./test-api.sh [delay] [title] [priority]

# --- HARDCODED CONFIGURATION ---
API_URL="" -> thay bằng link App Runner của bạn
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

Hãy tạo một tệp tin `.sh` với mã nguồn trên (sau khi thay thế `$API_URL` bằng URL App Runner của bạn) và thực thi nó để thấy tin nhắn được đưa vào hàng đợi.

Chạy với 

```bash
./test-api.sh 10 "High Priority Task" "High"
```

---

#### 2. Kiểm chứng qua giao diện Web (Validation through Web)

Hình ảnh dưới đây minh họa cách cơ chế hàng đợi hoạt động song song với các cập nhật WebSocket thời gian thực:

![Giao diện Web UI](/images/8-1/0001.jpeg)

Giao diện web cho phép bạn xác thực hệ thống theo các tiêu chí sau:
- **Cập nhật trạng thái trực tiếp**: Tin nhắn thay đổi từ `QUEUED` sang `COMPLETED` ngay khi được xử lý qua WebSocket.
- **Thống kê hàng đợi**: Xem phân phối tin nhắn theo các mức độ ưu tiên (High/Medium/Low).
- **Timeline xử lý**: Quan sát hành vi "bỏ qua" (bypass) hàng đợi trễ của các tin nhắn High Priority.
- **Trạng thái WebSocket**: Hiển thị kết nối đang hoạt động để nhận tin nhắn từ DynamoDB Streams.

Truy cập CloudFront URL đã tạo ở bước trước để mở giao diện này. Nếu hệ thống hoạt động đúng, bạn sẽ thấy tin nhắn "High Priority" được xử lý trước các tin nhắn độ ưu tiên thấp hơn dù có thời gian chờ (delay) giống nhau.
