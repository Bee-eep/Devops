# AWS DevOps Semester 4 Tasks

Welcome to the AWS DevOps Semester 4 Tasks repository! This project contains a series of hands-on AWS infrastructure and security exercises, each organized in its own folder. Every task is designed to help you build practical skills in cloud architecture, automation, and best practices.

## Tasks Overview

- **Task 1:** Secure access to private EC2 instances using a Bastion Host.
- **Task 2:** Implement Auto Scaling Groups (ASG) for dynamic EC2 management.
- **Task 3:** Configure Application Load Balancer (ALB) with path-based routing.
- **Task 4:** Set up DNS and traffic routing using AWS Route 53.
- **Task 5:** Create a custom IAM policy for controlled EC2 instance management.
- **Task 6:** Establish cross-account VPC peering for secure network connectivity.

Each folder contains detailed instructions and diagrams for its respective task. Use these exercises to deepen your understanding of AWS services and DevOps workflows.

---

Here’s an improved and more structured version of your README for the **AWS DevOps Semester 4 Tasks** repository:

---

# 🚀 AWS DevOps Semester 4 Tasks

Welcome to the **AWS DevOps Semester 4 Tasks** repository!
This repository serves as a curated collection of hands-on exercises aimed at building a strong foundation in cloud infrastructure, automation, and DevOps best practices using **Amazon Web Services (AWS)**.

Each task is thoughtfully designed to provide real-world experience with key AWS services and architecture patterns essential for any aspiring cloud or DevOps engineer.

---

## 📁 Repository Structure

The repository is organized into folders by task.
Each task folder contains:

* ✅ Step-by-step implementation guide
* 🧠 Conceptual overview
* 📊 Architecture diagram (where applicable)
* ⚙️ Terraform or AWS CLI snippets (if required)

---

## 📌 Task List & Descriptions

### 🔐 Task 1: Secure EC2 Access with a Bastion Host

Learn how to safeguard private EC2 instances by setting up a **Bastion Host** within a public subnet. This allows secure SSH access to instances in private subnets, following the principle of least privilege.

---

### 📈 Task 2: Auto Scaling Group (ASG) for EC2 Instances

Implement **Auto Scaling Groups** to automatically scale your EC2 instances based on demand. Understand how launch configurations, target groups, and scaling policies work together for high availability.

---

### 🌐 Task 3: Application Load Balancer with Path-Based Routing

Set up an **Application Load Balancer (ALB)** to distribute incoming traffic based on URL paths. Route requests to different target groups (e.g., `/api`, `/admin`, `/frontend`) based on rules.

---

### 🌍 Task 4: DNS Management Using AWS Route 53

Use **Route 53** to register domain names and manage DNS records. Learn how to configure routing policies and integrate Route 53 with other AWS services for resilient traffic distribution.

---

### 🔒 Task 5: Custom IAM Policy for EC2 Access Control

Create a **custom IAM policy** to restrict access to EC2 instances based on tags, regions, or specific actions. Gain a deeper understanding of identity-based policies and fine-grained permissions.

---

### 🔗 Task 6: Cross-Account VPC Peering

Establish **VPC Peering** between different AWS accounts to enable secure and private network communication. Learn the process of request/accept flow, route table updates, and DNS resolution across VPCs.

---

## 🎯 Goals

* Understand secure AWS networking practices
* Automate scalable infrastructure with minimal manual intervention
* Apply IAM and security principles for least-privilege access
* Gain real-world experience with infrastructure components and routing techniques

---

## 🧰 Prerequisites

* Basic knowledge of AWS services (EC2, VPC, IAM, etc.)
* Familiarity with the AWS Management Console and/or CLI
* Optional: Knowledge of Terraform or CloudFormation

---

## 📝 Getting Started

1. Clone this repository
2. Navigate to the task folder you're working on
3. Follow the instructions in the README or Markdown file inside the folder
4. Test your setup and explore the concepts in depth
5. Cleanup resources after each task to avoid unnecessary AWS costs

---

## 📬 Feedback & Contributions

If you find issues or have suggestions to improve the tasks, feel free to open an issue or pull request. Collaboration and feedback are always welcome!

---

**Let’s build the cloud, one task at a time! ☁️⚙️**
