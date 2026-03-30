---
title : "Create API Gateway WebSocket"
date :  2025
weight : 3 
chapter : false
pre : " <b> 6.3 </b> "
---

#### Create API Gateway WebSocket

This service provides a unique URL so that the browser can maintain a continuous connection with the system.

1. Access **API Gateway** -> Select **Build** in the **WebSocket API** box.
![API Gateway Setup](/images/6-3/0001.png)
![API Gateway Setup](/images/6-3/0002.png)
![API Gateway Setup](/images/6-3/0003.png)
2. - **API name**: `simple-websocket-api`.
   - **Route selection expression**: `request.body.action`.
   - Click **Next**.
![API Gateway Setup](/images/6-3/0004.png)

3. **Add routes**: Add 2 routes: `$connect` and `$disconnect`. Click **Next**.
![API Gateway Setup](/images/6-3/0005.png)
4. **Attach integrations**: For both routes, select the Integration type as **Lambda** and choose the `WebSocketConnectionHandler` function created in step 6.2.
![API Gateway Setup](/images/6-3/0006.png)
5. Click **Next**, set the **Stage name** to `prod`. Click **Next**.
![API Gateway Setup](/images/6-3/0007.png)

6. **Review and create**: Review all settings and click **Create and deploy**.
![API Gateway Setup](/images/6-3/0008.png)
7. Finally, record the WebSocket URL, which will look like: `wss://<api-id>.execute-api.<region>.amazonaws.com/prod`.
![API Gateway Setup](/images/6-3/0009.png)
