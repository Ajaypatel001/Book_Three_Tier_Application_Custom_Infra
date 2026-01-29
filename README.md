# 🚀 Terraform AWS Three-Tier Application Deployment

This project provisions and deploys a **three-tier architecture** (Frontend + Backend + Database) on AWS using Terraform.

It follows Infrastructure as Code (IaC) principles for automated and repeatable deployments.

---

## 📦 Components Provisioned

- VPC & Networking  
- Bastion Host  
- Frontend & Backend EC2 Instances  
- Application Load Balancers  
- Auto Scaling Groups  
- Launch Templates  
- Amazon RDS (MySQL)  

---

## 🏗️ Architecture Overview

### ✅ Frontend
- EC2 instances behind a Frontend Application Load Balancer  
- Managed by an Auto Scaling Group  
- Communicates securely with the Backend ALB  

### ✅ Backend
- EC2 instances behind a Backend Application Load Balancer  
- Auto Scaling enabled  
- Connects to RDS using environment variables  

### ✅ Database
- Amazon RDS deployed in private subnets  
- Not publicly accessible  
- Designed for high security  

---

## ✅ Prerequisites

Make sure you have:

- Terraform >= 1.x  
- AWS CLI configured  
- AWS SSH Key Pair  
- Application build artifacts  

---

## 🚀 Deployment Flow

### Step 1: Initialize Terraform
```bash
terraform init
