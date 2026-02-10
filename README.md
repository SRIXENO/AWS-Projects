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

# Detailed Project Implementations

---

## Project 1: Cloud-Based Static Website Hosting with Automated Monitoring using AWS

### 📌 Overview
This project focuses on designing and deploying a scalable static website hosting solution using Amazon Web Services (AWS).

### Technologies Used
- Amazon S3  
- Amazon EC2  
- AWS Lambda  
- Amazon SNS  
- IAM Roles  
- VPC  
- Apache / Nginx  
- HTML, CSS, JavaScript  

### Description
The system uses Amazon S3 for hosting static website files such as HTML, CSS, and JavaScript. A custom Virtual Private Cloud (VPC) was created to isolate the network and securely deploy an EC2 instance acting as a web server and log storage system.

An IAM role was configured to allow secure interaction between EC2 and S3 services. AWS Lambda was implemented to monitor file uploads in the S3 bucket and trigger automated alerts through Amazon SNS.

### Key Features
- Static website hosting using S3  
- Automated file synchronization  
- Real-time upload monitoring using Lambda  
- Secure cloud networking using VPC  
- Alert notification system using SNS  

---

## Project 2: Scalable WordPress Deployment using AWS EC2, RDS, S3, and VPC Architecture

### 📌 Overview
This project involves deploying a highly available and scalable WordPress web application using AWS cloud infrastructure.

### Technologies Used
- Amazon EC2  
- Amazon RDS (MySQL/MariaDB)  
- Amazon S3  
- IAM Roles  
- VPC Networking  
- WordPress  
- Linux Server  

### Description
The architecture includes a custom VPC with public and private subnets to ensure secure and controlled communication between services.

Amazon EC2 hosts the WordPress application, while Amazon RDS is configured in a private subnet to manage database operations securely. Amazon S3 is integrated for storing and managing media uploads, ensuring durability and scalability. IAM roles and security groups were configured to implement access control and network security.

### Key Features
- Scalable WordPress deployment  
- Secure database configuration using RDS  
- Media storage using S3  
- Role-based access control using IAM  
- Secure networking using VPC and security groups  

---

## Project 3: Secure Cloud File Storage System with Expiring Download Links using AWS

### 📌 Overview
This project implements a secure file storage and sharing system using AWS cloud services.

### Technologies Used
- Amazon EC2  
- Amazon S3  
- Amazon RDS  
- AWS Lambda  
- Amazon SES / SNS  
- IAM Roles  
- Python (Flask / Boto3)  

### Description
The web application is hosted on an EC2 instance, while Amazon S3 is used for storing uploaded files. Amazon RDS stores user credentials and file metadata.

AWS Lambda functions generate time-limited pre-signed URLs that allow users to securely download files. Email notifications were configured using AWS SES or SNS. The system also incorporates IAM roles, security groups, and optional VPC endpoints to enhance security and data protection.

### Key Features
- Secure cloud file storage  
- Expiring download link generation  
- Email notification system  
- Metadata storage using RDS  
- Serverless automation using Lambda  
- Strong IAM-based security implementation  

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

## Learning Objectives

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
