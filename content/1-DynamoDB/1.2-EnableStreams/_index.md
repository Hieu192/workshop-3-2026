---
title : "Enable DynamoDB Streams"
date :  2025
weight : 2 
chapter : false
pre : " <b> 1.2 </b> "
---

#### Enable DynamoDB Streams

This is a critical mechanism: Every time a record in DynamoDB changes, an "event" is sent out, allowing the system to synchronize data in Real-time.

1. From the Tables list, click on the name of the `PriorityItemsTable` you just created.
![DynamoDB Table](/images/1-2/0001.png)
2. Switch to the **Exports and streams** tab.
![DynamoDB Table](/images/1-2/0002.png)
3. Scroll down to the **DynamoDB stream details** section and click the **Turn on** button.
![DynamoDB Table](/images/1-2/0003.png)
4. In the window that appears, select **New image** (to transmit the entire latest data whenever there is a change), then click **Turn on stream**.
![DynamoDB Table](/images/1-2/0004.png)
![DynamoDB Table](/images/1-2/0005.png)

---
*Note: This DynamoDB stream will later be monitored by a Lambda function to send notifications via WebSocket.*
