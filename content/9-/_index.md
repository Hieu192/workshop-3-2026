---
title : "Resource Cleanup"
date :  2025
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Resource Cleanup

We will proceed to clean up the resources created from this workshop:

- From the **AWS Console** of **IAM role - ec2-admin-team-alpha**, click on the role name in the upper right corner and select **Switch back**.

![AWS IAM](/images/updateimage/77.png)

- Access the **IAM** service via the URL - https://console.aws.amazon.com/iam/.
- In the left navigation bar, select **Roles** and find **ec2-admin-team-alpha**.

![AWS IAM](/images/updateimage/78.png)

- Select **ec2-admin-team-alpha** and click the **Delete role** button.

![AWS IAM](/images/updateimage/79.png)

- In the left navigation bar, select **Policies** and find the following policies one by one, then click the **Delete policy** button.
  - ec2-list-read
  - ec2-create-tags
  - ec2-create-tags-existing
  - ec2-run-instances
  - ec2-manage-instances
  - Do the same with other policies.

![AWS IAM](/images/updateimage/80.png)

![AWS IAM](/images/updateimage/81.png)



- In the left navigation bar, select **User**, choose **AdminUser** and click **Delete**

![AWS IAM](/images/updateimage/88.png)

- Type **confirm** and click **Delete user**

![AWS IAM](/images/updateimage/89.png)