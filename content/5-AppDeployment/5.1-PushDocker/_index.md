---
title : "Push Source Code to ECR"
date :  2025
weight : 1 
chapter : false
pre : " <b> 5.1 </b> "
---

#### Push Source Code to Amazon ECR

1. **Download and prepare Backend source code**:
   - First, download the Spring Boot source code zip file here: [spring-app.zip](/spring-app.zip)
   - After downloading, extract it on your computer.
   - Open a terminal in the extracted `spring-app` directory.
![ECR View Push Commands](/images/5-1/0001.png)

2. Build the code into a JAR file:
```bash
mvn clean package -DskipTests
```
![ECR View Push Commands](/images/5-1/0002.png)

- This is the .jar file after building the code.
![ECR View Push Commands](/images/5-1/0003.png)

3. Access the AWS Console, go to the **Amazon ECR** service -> **Repositories** -> **Create repository**.
   - **Repository name**: Enter `priority-spring-app`.
   - Click **Create repository**.
![ECR View Push Commands](/images/5-1/0004.png)
![ECR View Push Commands](/images/5-1/0005.png)
![ECR View Push Commands](/images/5-1/0006.png)

4. Open the created repository and click the **View push commands** button in the top right corner. Run the 4 commands displayed in that window one by one in your terminal to push the image to AWS.
![ECR View Push Commands](/images/5-1/0007.png)
![ECR View Push Commands](/images/5-1/0008.png)

- You must remember to open Docker Desktop before running the commands, otherwise, you will get an error as shown below:
![ECR View Push Commands](/images/5-1/0009.png)
![ECR View Push Commands](/images/5-1/0010.png)
![ECR View Push Commands](/images/5-1/0011.png)

5. After running the 4 commands, check ECR again to see the results as follows:
![ECR View Push Commands](/images/5-1/0012.png)
