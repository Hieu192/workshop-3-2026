---
title : "Initialize Broker"
date :  2025
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

#### Initialize Amazon MQ Broker

1. Search for and access the **Amazon MQ** service on the Console.
![Amazon MQ Setup](/images/2-1/0001.png)
2. Select **Create broker**.
![Amazon MQ Setup](/images/2-1/0002.png)
3. In the **Select broker engine** step, choose **Apache ActiveMQ** and click **Next**.
![Amazon MQ Setup](/images/2-1/0003.png)
4. In the **Select deployment and storage** step, choose **Single-instance broker** (to save costs for the lab) and click **Next**.
![Amazon MQ Setup](/images/2-1/0004.png)

5. In the **Configure settings** section:
- **Broker name**: Enter `PriorityMessageBroker`
- **Broker instance type**: Select `mq.t3.micro`
- **ActiveMQ Web Console access**: Switch to **Yes**
- **Username**: Enter `admin`
- **Password**: `MyP@ssw0rd2025!` (Note: You should choose a stronger password).
![Amazon MQ Setup](/images/2-1/0005.png)
- Next, scroll to the bottom and click **Next**.
![Amazon MQ Setup](/images/2-1/0006.png)

6. In the **Review and create** section, review your settings and click **Create broker**.
![Amazon MQ Setup](/images/2-1/0007.png)
![Amazon MQ Setup](/images/2-1/0008.png)

7. Once created, wait about 15-20 minutes for the Broker status to change to **Running**.
![Amazon MQ Setup](/images/2-1/0009.png)
