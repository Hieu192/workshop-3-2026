---
title : "Password Storage with AWS Secrets Manager"
date :  2025
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

### Section Overview

According to AWS security standards, backend systems should not keep passwords directly in the source code. We will store this Broker password in **Secrets Manager**.

Main topics in this section:
- Create a new Secret containing Amazon MQ login information.
- Name it to match the source code configuration.

![Secrets Manager Logo](/images/3/00001.png)

#### Create a Secret for the Broker

To avoid hardcoding the Broker password directly into the source code, we will store the password in **Secrets Manager**.

1. Search for and access the **Secrets Manager** service.
![Secrets Manager Logo](/images/3/0002.png)
2. Click the **Store a new secret** button.
![Secrets Manager Logo](/images/3/0003.png)
3. In the **Secret type** section, select **Other type of secret**. Switch to the **Plaintext** tab and enter the JSON content containing the MQ login information:
   ```json
   {
     "username": "admin",
     "password": "MyP@ssw0rd2025!"
   }
   ```
![Secrets Manager Logo](/images/3/0004.png)
   - Continue scrolling to the bottom and select **Next**.
![Secrets Manager Logo](/images/3/0005.png)
4. In the **Configure secret** section:
   - Secret name: `MessagingStack-MessagingMqPassword` (This name must exactly match the `@Value` configuration in Spring Boot).
   - Description: `Password for Amazon MQ Broker`
![Secrets Manager Logo](/images/3/0006.png)
   - Continue scrolling to the bottom and select **Next**.
![Secrets Manager Logo](/images/3/0007.png)

5. In the **Configure rotation** section, select **Disable automatic rotation** (default). Click **Next**.
![Secrets Manager Logo](/images/3/0008.png)

6. In the **Review** section, check the information and click **Store**.
![Secrets Manager Logo](/images/3/0009.png)
![Secrets Manager Logo](/images/3/0010.png)

---
*Note: Centralized password management through Secrets Manager allows us to easily change passwords periodically without rebuilding the code.*
