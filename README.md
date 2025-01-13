# AWS 3-Tier Architecture Deployment
## Overview
#### This project demonstrates the deployment of a secure and scalable 3-tier architecture on AWS, featuring web, application, and database tiers. It utilizes key AWS services such as VPC, EC2, RDS, S3, and Route 53 to ensure high availability, security, and fault tolerance.

## Architecture Diagram
![3-Tier Cloud Application Architecture](https://github.com/Dipesh001m/3tier-cloud-app/blob/main/Diagram.png)

### Technologies Used
AWS Services: VPC, EC2, RDS, S3, IAM, Route 53, Certificate Manager
Configuration Tools: AWS Management Console, AWS CLI
Deployment Strategy: Multi-AZ Deployment
Security: SSL Certificates, IAM Roles, Private Subnets
Steps to Deploy

### 1. Set Up the VPC and Subnets
Create a VPC with:
CIDR block: 10.0.0.0/16
Create public and private subnets:
Public Subnets (for web and ALB): 10.0.1.0/24
Private Subnets (for application and database): 10.0.2.0/24
Attach an Internet Gateway (IGW) to the VPC.
Configure Route Tables:
Associate the public route table with public subnets and route traffic via the IGW.

### 2. Deploy EC2 Instances
Launch EC2 instances for:
Web Tier: Public Subnet
Application Tier: Private Subnet
Assign appropriate IAM roles to the instances for secure access.
Configure Security Groups:
Allow HTTP/HTTPS traffic for web-tier EC2.
Restrict application-tier EC2 to receive traffic only from the web tier.

### 3. Set Up the RDS Instance
Create an RDS database (e.g., MySQL or PostgreSQL) in the private subnet with:
Multi-AZ deployment for fault tolerance.
Automated backups enabled.
Configure the application-tier EC2 to connect securely to the RDS instance.

### 4. Configure S3 for Static Storage
Create an S3 bucket to store static assets or application files.
Apply bucket policies to control access:
Public access for web-tier assets.
Private access for application-tier backups.

### 5. Secure the Architecture
Use AWS Certificate Manager to provision SSL certificates for the web tier.
Configure HTTPS in the web-tier EC2 and Load Balancer (ALB).

### 6. Manage DNS with Route 53
Create a Route 53 Hosted Zone for your domain.
Add A/ALIAS records to route traffic to the ALB.
Verify DNS resolution for your domain.

