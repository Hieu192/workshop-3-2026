---
title : "Create IAM Role"
date :  2025
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

#### Create IAM Role

We will proceed to create an IAM role for the **EC2 Administrator** user along with the policies created in the previous section.

1. Log in to **AWS Management Console** and access **IAM Management Console**.

2. In the left navigation bar, select Role and click **Create role** button.

![AWS IAM](/images/updateimage/37.png)

3. On the create new screen, we select **Another AWS account** and fill in our **account ID** (you can find **Account ID** in the **My Account** section). Select **Next**

![AWS IAM](/images/updateimage/34.1.png)

{{% notice tip %}} To enhance security, you can enable **Require MFA**
{{% /notice %}}

![AWS IAM](/images/updateimage/38.1.png)

In the **Attach permissions policies** area, we will select the following policies in order:

   - ec2-list-read
   - ec2-create-tags
   - ec2-create-tags-existing
   - ec2-run-instances
   - ec2-manage-instances


![AWS IAM](/images/updateimage/83.png)

4. Select **Next**.

5. Fill in the name ```ec2-admin-team-alpha``` with specific description.

![AWS IAM](/images/updateimage/41.1.png)

6. Proceed to create by clicking Create role.

![AWS IAM](/images/updateimage/85.png)

7. After successful creation, in the list of **IAM roles**, we select **ec2-admin-team-alpha**.

![AWS IAM](/images/updateimage/43.png)

8. We proceed to configure **Trust relationships**.

![AWS IAM](/images/updateimage/44.png)

9. Edit the **trust policy** and click **Update policy**

         arn:aws:iam:<Account ID>:user/AdminUser

![AWS IAM](/images/updateimage/87.png)

![AWS IAM](/images/updateimage/46.png)

10. Complete the update.

![AWS IAM](/images/updateimage/90.png)
