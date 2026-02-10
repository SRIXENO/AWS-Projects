# AWS Multi-Tier Cloud Infrastructure Projects

## 📌 Project Overview

This repository demonstrates real-world **AWS cloud architecture implementations** built using core AWS services. The project focuses on designing secure, scalable, and cost-efficient cloud solutions following DevOps and cloud best practices.

---

## 📌 AWS Free Tier Notice ⚠️

This project was implemented using **AWS Free Tier resources**.

- Only free-tier eligible services were used  
- Instances like `t2.micro / t3.micro` were selected  
- Limited storage and compute resources were used  
- Due to cost safety, this repository contains **architecture screenshots and configuration images instead of running production services**  
---

## Implemented Architectures

- ✔ Static Website Hosting using Amazon S3  
- ✔ WordPress Deployment using EC2 + RDS + S3  
- ✔ Secure File Storage System using EC2 + Lambda + RDS + S3  
- ✔ Custom VPC Network Setup  
- ✔ IAM Role Based Secure Access  

---

## Tech Stack & AWS Services

- Amazon EC2  
- Amazon S3  
- Amazon RDS  
- AWS Lambda  
- AWS IAM  
- Amazon SNS / SES  
- Amazon VPC  
- Amazon EBS  
- Python (Boto3)  
- Linux (Amazon Linux / Ubuntu)  

---

## Key Features

- Multi-tier cloud architecture design  
- Serverless automation workflows  
- Secure networking using VPC & Security Groups  
- Role-based authentication using IAM  
- Automatic file synchronization  
- Pre-signed URL secure file sharing  
- WordPress CMS deployment with database separation

---

## 🎯 Learning Objectives

- Cloud Infrastructure Design  
- DevOps Automation  
- AWS Networking & Security  
- Serverless Computing  
- Scalable Web Application Deployment  

---

# Overall AWS Architecture

```mermaid
flowchart TD

User -->|Access Website| EC2

subgraph VPC [Custom VPC 10.0.0.0/16]
    
    subgraph Public_Subnet [Public Subnet]
        EC2[EC2 Web Server]
    end
    
    subgraph Private_Subnet [Private Subnet]
        RDS[(RDS Database)]
    end
end

EC2 -->|Store Files| S3[(Amazon S3 Bucket)]
EC2 -->|Read/Write Metadata| RDS

S3 -->|Trigger Event| Lambda[Lambda Function]
Lambda -->|Send Notification| SNS[SNS / SES Email Alerts]

IAM[IAM Roles & Policies] --> EC2
IAM --> Lambda
