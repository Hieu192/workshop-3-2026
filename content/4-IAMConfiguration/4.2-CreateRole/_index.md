---
title : "Create Role for App Runner"
date :  2025
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---

#### Create Instance Role

After creating the Policy, we need to attach it to a Role so that App Runner can assume these permissions when launching the Backend.

1. In the IAM menu on the left, select **Roles** -> **Create role**.
![IAM Role Create](/images/4-2/0001.png)
2. **Trusted entity type**: Select **Custom trust policy**. Paste the following code:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "build.apprunner.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```
![IAM Role Create](/images/4-2/0002.png)

3. In the **Add permissions** box, search for the `AppRunnerPriorityPolicy` created in step 4.1 and select it. Click **Next**.
![IAM Role Create](/images/4-2/0003.png)

4. In **Name, Review, and Create**, name the Role as `AppRunnerPriorityInstanceRole`.
![IAM Role Create](/images/4-2/0004.png)
5. Click **Create role**.
![IAM Role Create](/images/4-2/0005.png)
![IAM Role Create](/images/4-2/0006.png)
