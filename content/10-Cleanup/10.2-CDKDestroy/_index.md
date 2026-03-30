---
title : "Automated Cleanup (Script & CDK)"
date :  2025
weight : 2 
chapter : false
pre : " <b> 10.2 </b> "
---

### Fully Automated Cleanup (Recommended)

If you deployed the application using `deploy.sh`, the cleanup script `destroy.sh` is the safest and most thorough way to remove all resources without encountering errors like "Bucket not empty" or "ECR contains images."

#### 1. Run the Cleanup Script
In the root directory of the project, use Git Bash (on Windows) and run the command:
```bash
bash destroy.sh
```

**This script will automatically perform:**
- **Empty S3 Bucket**: Delete all data and versions of the Frontend before deleting the Bucket.
- **Delete ECR Images**: Clean up Docker builds in AWS ECR.
- **Delete CloudFront OAC & WAF**: Remove CDN-specific security configurations.
- **cdk destroy --all**: Delete all CloudFormation Stacks (VPC, MQ, App Runner, etc.) in the correct reverse dependency order.

#### 2. Cleanup using only CDK (Alternative)
If you only want to delete infrastructure Stacks without deep-cleaning S3/ECR data:
1. Navigate to the `/infra` directory.
2. Run the command: `cdk destroy --all`

---
🎉 **CONGRATULATIONS! YOU HAVE COMPLETED THE ENTIRE PRIORITY-BASED MESSAGE PROCESSING WORKSHOP ON AWS!**
