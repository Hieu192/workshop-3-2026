---
title : "Create Table"
date :  2025
weight : 1 
chapter : false
pre : " <b> 1.1 </b> "
---

#### Create DynamoDB Table

1. Log in to the **AWS Management Console**.
2. In the search bar at the top, type **DynamoDB** and select the DynamoDB service.
![DynamoDB Table](/images/1-1/0001.png)
3. On the left menu, select **Tables**, then click the orange **Create table** button.
![DynamoDB Table](/images/1-1/0002.png)
4. In the **Table details** section:
   - **Table name**: Enter `PriorityItemsTable`
   - **Partition key**: Enter `id` (ensure the data type is `String`)
![DynamoDB Table](/images/1-1/0003.png)
5. In the **Table settings** section, leave as **Default settings**.
![DynamoDB Table](/images/1-1/0005.png)
6. Scroll to the bottom and select **Create table**. Wait about 1-2 minutes for the table status to change to *Active*.

![DynamoDB Table](/images/1-1/0006.png)
