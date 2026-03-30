---
title : "Create Policy"
date :  2025
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

#### Create Policy for App Runner

The App Runner service (Backend) needs permissions to access the DynamoDB table and decrypt passwords from Secrets Manager.

1. Access the **IAM** service -> **Policies** -> **Create policy**.
![IAM Policy Create](/images/4-1/0001.png)
![IAM Policy Create](/images/4-1/0002.png)
2. Select the **JSON** tab and paste the following code (to grant access to the DB table and retrieve the Secret):
   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "dynamodb:PutItem",
                   "dynamodb:GetItem",
                   "dynamodb:UpdateItem",
                   "dynamodb:DeleteItem",
                   "dynamodb:Scan"
               ],
               "Resource": "*"
           },
           {
               "Effect": "Allow",
               "Action": "secretsmanager:GetSecretValue",
               "Resource": "*"
           }
       ]
   }
   ```
![IAM Policy JSON](/images/4-1/0003.png)
3. Click **Next**, name the Policy as `AppRunnerPriorityPolicy`, and click **Create policy**.

![IAM Policy Create](/images/4-1/0004.png)
