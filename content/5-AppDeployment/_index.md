---
title : "Check Policy"
date :  2025
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

#### Check Policy


Let's review the brief description of each IAM Policy:

- **ec2-list-read**: This policy will only allow read-only permissions for EC2 service in regions **us-east-1** and **us-west-1**
- **ec2-create-tags**: This policy will allow creating tags for EC2 service, with the execution condition being when we proceed to create an EC2 instance
- **ec2-create-tags-existing**: This policy will allow creating tags for EC2 service, with the condition being when and only when resources (already existing or to be newly created) are assigned tags as follows **"Key=Team,Value=Alpha"**
- **ec2-run-instances**: This policy allows creating EC2 instances when and only when conditions about AWS Regions (**us-east-1 & us-west-1**) and Resource Tags (**Key=Team,Value=Alpha**) are satisfied. Next, this policy allows creating related resources at the time we proceed to create EC2 instance, with conditions about AWS Regions (**us-east-1 & us-west-1**).
- **ec2-manage-instances**: This policy allows performing basic operations (reboot, terminate, start, stop) on EC2 instances, with conditions that AWS Regions (**us-east-1 & us-west-1**) and Resource Tags (**Key=Team,Value=Alpha**) must be satisfied.
