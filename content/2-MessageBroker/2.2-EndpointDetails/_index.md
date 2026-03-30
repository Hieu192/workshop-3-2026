---
title : "Record Endpoint URL"
date :  2025
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

#### Retrieve Endpoint Parameters

The Broker initialization process can take up to 15-20 minutes. Once the status is **Running**, click on your Broker's name.

1. Locate the **Endpoints** section.
![Broker Endpoints](/images/2-2/0001.png)
2. Copy the URL for the **OpenWire** protocol (the protocol starting with `ssl://...`). Example: `ssl://b-12345-1.mq.us-east-1.amazonaws.com:61617`.
![Broker Endpoints](/images/2-2/0002.png)
3. Keep this parameter carefully; this is the URL you will need to enter into the Spring Boot environment variables in the following sections.

4. Add a rule to the Security Group to allow App Runner access as follows:
    - Type: Custom TCP
    - Port Range: 61617
    - Source: Select 0.0.0.0/0 (To allow App Runner access from the Internet).
    - Description: Allow App Runner to ActiveMQ
![Broker Endpoints](/images/2-2/0003.png)
![Broker Endpoints](/images/2-2/0004.png)
![Broker Endpoints](/images/2-2/0005.png)
