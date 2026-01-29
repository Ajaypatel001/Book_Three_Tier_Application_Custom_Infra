# 🚀 Terraform AWS Application Deployment

This project provisions and deploys a **three-tier architecture** (Frontend + Backend + Database) on AWS using **Terraform**.
It follows Infrastructure as Code (IaC) practices to automate infrastructure deployment and ensure scalability, security, and high availability.

---

## 📦 Components Provisioned

* VPC & Networking
* Bastion Host
* Frontend & Backend EC2 Instances
* Application Load Balancers
* Auto Scaling Groups
* Launch Templates
* Amazon RDS (MySQL)

---

## 🏗️ Architecture Overview

### ✅ Frontend

* EC2 instances deployed behind a Frontend Application Load Balancer
* Managed using an Auto Scaling Group
* Communicates securely with the Backend ALB

### ✅ Backend

* EC2 instances deployed behind a Backend Application Load Balancer
* Auto Scaling enabled for high availability
* Connects to Amazon RDS using environment variables

### ✅ Database

* Amazon RDS (MySQL) deployed in private subnets
* Not publicly accessible
* Designed with security best practices

---

## ✅ Prerequisites

Ensure the following tools and configurations are ready before deployment:

* Terraform >= 1.x
* AWS CLI configured
* AWS SSH Key Pair
* Application build artifacts

---

## 🚀 Deployment Flow

### 🔹 Step 1: Initialize Terraform

```bash
terraform init
```

---

### 🔹 Step 2: Apply Networking

```bash
terraform plan -target=module.networking
terraform apply -target=module.networking
```

---

### 🔹 Step 3: Deploy Bastion Host

```bash
terraform apply -target=module.bastion
```

---

### 🔹 Step 4: Deploy EC2 Instances

```bash
terraform plan -target=module.frontend_ec2
terraform apply -target=module.frontend_ec2

terraform plan -target=module.backend_ec2
terraform apply -target=module.backend_ec2
```

---

### 🔹 Step 5: Deploy Load Balancers

```bash
terraform plan -target=module.backend_alb
terraform apply -target=module.backend_alb

terraform plan -target=module.frontend_alb
terraform apply -target=module.frontend_alb
```

---

### 🔹 Step 6: Deploy Database

```bash
terraform plan -target=module.database
terraform apply -target=module.database
```

---

### 🔹 Step 7: Apply Remaining Modules

```bash
terraform plan -target=module.frontend_launch_template
terraform apply -target=module.frontend_launch_template

terraform plan -target=module.backend_launch_template
terraform apply -target=module.backend_launch_template

terraform plan -target=module.backend_asg
terraform apply -target=module.backend_asg

terraform plan -target=module.frontend_asg
terraform apply -target=module.frontend_asg
```

---

## 🌐 Application Deployment

### 🔹 Backend

* Connect via Bastion Host or create instances in a public subnet
* Deploy the backend application
* Configure RDS credentials in the `.env` file

### 🔹 Frontend

* Connect via Bastion Host or create instances in a public subnet
* Update the Backend Load Balancer URL
* Deploy the frontend application

---

## 🔐 Security Highlights

* Database hosted in private subnets
* Bastion host used for secure SSH access
* Minimal security group exposure
* No public access to RDS

---

## ⭐ Key Features

✔ Infrastructure as Code
✔ Modular Terraform Design
✔ Highly Scalable Architecture
✔ Production-Style AWS Setup

---

## 👨‍💻 Author

**Ajay Patel**
Cloud & DevOps Enthusiast 🚀
