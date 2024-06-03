# 🚀 Deploying a Static App from S3 to EC2 with VPC, Subnet, IAM, CodePipeline, and CodeDeploy

![image](https://github.com/SivaranjanAsokan/1.3.AWS_PROJECT_3_Web_Host_S3_CPipe_CDeploy/assets/163242501/61435d98-2e9c-4dcd-a8bd-1c000252fd86)

## Introduction
Deploying a static application from S3 to an EC2 instance can seem like a complex task. But with the right steps and tools, it becomes a straightforward process. In this guide, we'll walk through how to set up a VPC, subnet, IAM roles, and use CodePipeline and CodeDeploy to automate the deployment process. Let's get started! 🎉

![image](https://github.com/SivaranjanAsokan/1.3.AWS_PROJECT_3_Web_Host_S3_CPipe_CDeploy/assets/163242501/4f446dfb-cfdb-4c61-9555-e14f6037d603)


## Prerequisites
Before we begin, ensure you have the following:
- An AWS account
- Basic understanding of AWS services

## Step 1: Set Up Your VPC 🏗️
First, create a Virtual Private Cloud (VPC) to isolate your EC2 instance and other resources.

1. **Navigate to the VPC Dashboard:**
   - Open the VPC dashboard from the AWS Management Console.

2. **Create a VPC:**
   - Click on "Create VPC."
   - Name your VPC and provide an IPv4 CIDR block (e.g., `10.0.0.0/16`).

3. **Create Subnets:**
   - Create a public subnet for the EC2 instance (e.g., `10.0.1.0/24`).
   - Create a private subnet if needed (e.g., `10.0.2.0/24`).

4. **Internet Gateway:**
   - Attach an internet gateway to your VPC to allow internet access for your public subnet.

5. **Route Tables:**
   - Create and associate a route table with your public subnet.

## Step 2: Set Up IAM Roles and Policies 🛡️
IAM roles allow your EC2 instance to access other AWS services securely.

1. **Create an IAM Role for EC2:**
   - Navigate to the IAM dashboard and create a new role.
   - Choose "EC2" as the trusted entity.
   - Attach the `AmazonS3ReadOnlyAccess` policy to allow EC2 to read from S3.

2. **Create an IAM Role for CodeDeploy:**
   - Create another IAM role for CodeDeploy.
   - Attach the `AWSCodeDeployRole` policy.

## Step 3: Launch an EC2 Instance 🖥️
Launch an EC2 instance in your VPC's public subnet.

1. **Select AMI and Instance Type:**
   - Choose an appropriate Amazon Machine Image (AMI) and instance type.

2. **Configure Instance Details:**
   - Ensure your instance is launched within the VPC and subnet created earlier.
   - Attach the IAM role for EC2 to the instance.

3. **Security Groups:**
   - Create and configure security groups to allow necessary traffic (e.g., HTTP, SSH).

## Step 4: Set Up CodePipeline and CodeDeploy 🛠️
Now, we’ll set up CodePipeline and CodeDeploy to automate the deployment from S3 to EC2.

1. **Create an S3 Bucket:**
   - Create an S3 bucket to store your static app files.

2. **Create a CodeDeploy Application:**
   - Navigate to the CodeDeploy dashboard and create a new application.
   - Define a deployment group and specify the EC2 instance using tags.

3. **Create a CodePipeline:**
   - Navigate to the CodePipeline dashboard and create a new pipeline.
   - Choose S3 as the source provider and specify the bucket and path.
   - Add a deployment stage and choose CodeDeploy as the deployment provider.

## Step 5: Deploy Your Application 🚀
Finally, let's deploy the static app to the EC2 instance.

1. **Upload Files to S3:**
   - Upload your static app files (HTML, CSS, JS) to the S3 bucket.

2. **Trigger the Pipeline:**
   - CodePipeline will automatically detect changes in the S3 bucket and trigger the deployment.
   - CodeDeploy will deploy the static files to the EC2 instance.

3. **Verify Deployment:**
   - Access the EC2 instance via its public IP address to verify that the static app is running.

## Conclusion
By following these steps, you've successfully automated the deployment of a static app from S3 to an EC2 instance using VPC, Subnet, IAM, CodePipeline, and CodeDeploy. 🎉 This setup not only streamlines the deployment process but also ensures scalability and security.

Happy deploying! 🚀✨

---
