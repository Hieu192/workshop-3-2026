---
title : "Create IAM Policy"
date :  2025
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

#### Create IAM Policy

In the previous section, the **policies** will be divided into 5 different functions. If you want, you can freely edit and combine them to suit the practical requirements you are aiming for or want to apply.

#### Steps to Create IAM Policy

1. Log in to **AWS Management Console** and access **IAM Management Console**.

![AWS IAM](/images/updateimage/1.png)

2. In the left navigation bar, select **Policies** and click **Create policy** button.

![AWS IAM](/images/updateimage/14.png)

3. On the create new screen, we select **JSON** and fill in our policy specification. 

   - In this example, we use the **ec2-list-read** policy

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ec2listread",
            "Effect": "Allow",
            "Action": [
                "ec2:Describe*",
                "ec2:Get*"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:RequestedRegion": [
                        "us-east-1",
                        "us-west-1"
                    ]
                }
            }
        }
    ]
}
```

![AWS IAM](/images/updateimage/15.png)

4. Leave default configuration. Select **Next** to proceed with review.

![AWS IAM](/images/updateimage/16.png)

5. Fill in the name with specific description.

   - Name: **```ec2-list-read```**
   - Description: **```ec2-list-read```**
   - Proceed to create by clicking **Create Policy**.

![AWS IAM](/images/updateimage/17.png)

![AWS IAM](/images/updateimage/18.png)

6. **Policy** created successfully.

![AWS IAM](/images/updateimage/19.png)

#### Policy - ec2-create-tags

1. In the left navigation bar, select **Policies** and click **Create policy** button.

![AWS IAM](/images/updateimage/14.png)

2. On the create new screen, we select **JSON** and fill in our policy specification. In this example, we use the **ec2-create-tags** policy.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ec2createtags",
            "Effect": "Allow",
            "Action": "ec2:CreateTags",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ec2:CreateAction": "RunInstances"
                }
            }
        }
    ]
}
```

![AWS IAM](/images/updateimage/20.2.png)

3. Select **Next**.

![AWS IAM](/images/updateimage/20.3.png)

4. Information:
   - Name: **```ec2-create-tags```**
   - Description: **```ec2-create-tags```**
   - Description: This policy will allow creating tags for EC2 service, with the execution condition being when we proceed to create an **EC2 instance**.

![AWS IAM](/images/updateimage/20.1.png)

5. Proceed to create by clicking **Create Policy**.

![AWS IAM](/images/updateimage/24.png)

6. **Policy** created successfully.

![AWS IAM](/images/updateimage/20.4.png)

#### Policy - ec2-create-tags-existing

Information:

   - Name: **ec2-create-tags-existing**
   - Description: **ec2-create-tags-existing**
   - Description: This policy allows users to assign tags to EC2 service resources when all three conditions are met:
     - The tag assigned to the EC2 resource is the key-value pair **"Key=Team,Value=Alpha"**
     - The assigned tag key of the EC2 resource includes **Team and Name**
     - The tag requested to be assigned must be the key-value pair **"Key=Team,Value=Alpha"**

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ec2createtagsexisting",
      "Effect": "Allow",
      "Action": "ec2:CreateTags",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "aws:RequestTag/Team": "Alpha"
        },
        "ForAllValues:StringEquals": {
          "aws:TagKeys": [
            "Team",
            "Name"
          ]
        }
      }
    }
  ]
}
```
![AWS IAM](/images/updateimage/82.png)

![AWS IAM](/images/updateimage/20.6.png)

![AWS IAM](/images/updateimage/23.png)

![AWS IAM](/images/updateimage/24.png)

![AWS IAM](/images/updateimage/25.png)

#### Policy - ec2-run-instances
Information:

- **Name**: **ec2-run-instances**
- **Description:** **ec2-run-instances**
- **Description:** This policy will be divided into 2 parts:
- **First part:** Allows creating EC2 instances when and only when conditions about **AWS Regions** and **Resource Tags** are satisfied.
- **Remaining part:** Allows creating related resources at the time we proceed to create **EC2 instance**, with conditions about **AWS Regions**.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ec2runinstances",
            "Effect": "Allow",
            "Action": "ec2:RunInstances",
            "Resource": "arn:aws:ec2:*:*:instance/*",
            "Condition": {
                "StringEquals": {
                    "aws:RequestedRegion": [
                        "us-east-1",
                        "us-west-1"
                    ],
                    "aws:RequestTag/Team": "Alpha"
                },
                "ForAllValues:StringEquals": {
                    "aws:TagKeys": [
                        "Name",
                        "Team"
                    ]
                }
            }
        },
        {
            "Sid": "ec2runinstancesother",
            "Effect": "Allow",
            "Action": "ec2:RunInstances",
            "Resource": [
                "arn:aws:ec2:*:*:subnet/*",
                "arn:aws:ec2:*:*:key-pair/*",
                "arn:aws:ec2:*::snapshot/*",
                "arn:aws:ec2:*:*:launch-template/*",
                "arn:aws:ec2:*:*:volume/*",
                "arn:aws:ec2:*:*:security-group/*",
                "arn:aws:ec2:*:*:placement-group/*",
                "arn:aws:ec2:*:*:network-interface/*",

                "arn:aws:ec2:*::image/*"
            ],
            "Condition": {
                "StringEquals": {
                    "aws:RequestedRegion": [
                        "us-east-1",
                        "us-west-1"
                    ]
                }
            }
        }
    ]
}
```

![AWS IAM](/images/updateimage/26.png)

![AWS IAM](/images/updateimage/27.png)

![AWS IAM](/images/updateimage/28.png)

![AWS IAM](/images/updateimage/29.png)

![AWS IAM](/images/updateimage/30.png)

#### Policy - ec2-manage-instances
Information:

  - **Name**: ec2-manage-instances
  - **Description**: ec2-manage-instances
  - **Description**: This policy allows performing basic operations (reboot, terminate, start, stop) on EC2 instances, with conditions that AWS Regions and Resource Tags must be satisfied.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ec2manageinstances",
            "Effect": "Allow",
            "Action": [
                "ec2:RebootInstances",
                "ec2:TerminateInstances",
                "ec2:StartInstances",
                "ec2:StopInstances"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ec2:ResourceTag/Team": "Alpha",
                    "aws:RequestedRegion": [
                        "us-east-1",
                        "us-west-1"
                    ]
                }
            }
        }
    ]
}
```

![AWS IAM](/images/updateimage/31.png)

![AWS IAM](/images/updateimage/32.png)

![AWS IAM](/images/updateimage/33.png)

![AWS IAM](/images/updateimage/34.png)

![AWS IAM](/images/updateimage/35.png)


After completion, you will have 5 EC2 policies as below:

![AWS IAM](/images/updateimage/42.1.png)
