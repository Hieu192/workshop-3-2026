---
title : "Introduction"
date :  2025
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Overview

This workshop will take us through the process of managing **EC2** service access using **Resource Tags** through detailed configuration of IAM policies and roles with specific permissions. Using **Resource Tags** will be extremely useful as we gradually scale up in permission management.

In this workshop, we will create policies along with roles that can be used for certain users, such as **EC2 Administrator**. These policies will only allow EC2 Administrator to create related resources when they meet the stated requirements and are based on certain Resource Tags.

#### Objectives

- IAM least privilege (**IAM least privilege**)
- Specify IAM policies with conditions (**IAM policy conditions**)

#### Prerequisites

- An AWS account used for **Testing** purposes.
- An IAM user (**with MFA configured**) capable of performing **assume role** tasks.
