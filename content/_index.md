---
title : "Managing EC2 Resource Tag Access with AWS IAM"
date : 2025
weight : 1
chapter : false
---

# Managing EC2 Resource Tag Access with AWS IAM

#### Overview

This workshop will guide us through the process of managing EC2 service access with **Resource Tags** through detailed configuration of policies and IAM roles with specific **permissions**. Using **Resource Tags** will be extremely useful when we scale up in decentralized management.

In this workshop, we will create policies with roles that can be used by certain users, such as **EC2 Administrators**. These **policies** will only allow EC2 Administrators to create related resources when they meet the stated requirements and are based on certain **Resource Tags**.

{{< figure src="../images/serviceicon2.png" title="AWS IAM" width=150pc >}}

#### Objectives

- Apply IAM least privilege method.
- Specify IAM policies with detailed conditions (**IAM Policy Conditions**)

#### Prerequisites

- AWS account used for **Testing** purposes.
- **IAM User** (MFA configured) capable of performing **assume role** tasks.

{{% notice info %}}
This lab will not be suitable if your account only has access to one Region.
{{% /notice %}}
