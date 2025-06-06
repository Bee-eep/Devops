# Task 1: Establish Connectivity to Private EC2 Instance from Public EC2 (Bastion Host)

## 📋 Overview
Amazon EC2 provides scalable virtual servers in AWS cloud. In production environments, private EC2 instances require secure access through a **Bastion Host** - a hardened public EC2 instance acting as a secure gateway.

## 🏗️ Architecture
- **Bastion Host**: Public subnet + Internet Gateway (IGW)
- **Target Instance**: Private subnet (no direct internet access)
- **Access Flow**: Local machine → Bastion Host → Private EC2

---

## 🚀 Implementation Steps

### 1️⃣ VPC Configuration
![VPC Configuration](image.png)

### 2️⃣ Subnet Setup

#### Public Subnet
![Public Subnet Configuration](image-1.png)

#### Private Subnet
![Private Subnet Configuration](image-2.png)

### 3️⃣ Internet Gateway Deployment
![Internet Gateway Setup](image-3.png)

### 4️⃣ SSH Connection to Private Instance
![SSH Connection Process](image-4.png)