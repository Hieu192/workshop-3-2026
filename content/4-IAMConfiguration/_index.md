---
title : "Configure Application Permissions (IAM Role)"
date :  2025
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

#### Section Overview

Our Backend (App Runner) needs permissions to read DynamoDB and decrypt passwords from Secrets Manager. We will accomplish this through the Role and Policy mechanism.

Main topics in this section:
- Create a permission policy (Policy JSON) containing read permissions for the DB and Secrets.
- Create a Role for App Runner and attach that policy to it.

![IAM Overview](/images/4/0001.png)
