# AWS DevOps Semester 4 Tasks

Welcome to the **AWS DevOps Semester 4 Tasks** repository.

This repository provides a collection of structured, hands-on exercises designed to strengthen your skills in AWS cloud infrastructure, automation, and DevOps practices. Each task focuses on solving real-world scenarios using industry-relevant tools and concepts.

---

## Repository Structure

Each task is organized into its own folder and typically includes:

- Step-by-step implementation guide  
- Conceptual explanation  
- Architecture diagram (if applicable)  
- Terraform configurations or AWS CLI commands  

---

## Task Descriptions

### Task 1: Secure EC2 Access with a Bastion Host

Configure a Bastion Host in a public subnet to allow secure SSH access to EC2 instances located in private subnets. This task introduces network isolation and best practices for access control using jump hosts.

---

### Task 2: Auto Scaling Group (ASG) for EC2 Instances

Set up Auto Scaling Groups to automatically scale EC2 instances based on defined metrics or schedules. Learn how to configure launch templates, attach target groups, and apply scaling policies for fault tolerance and cost optimization.

---

### Task 3: Application Load Balancer with Path-Based Routing

Deploy an Application Load Balancer that routes traffic based on URL paths. Configure listener rules to direct traffic to different target groups (such as `/api`, `/admin`, or `/frontend`) and enhance your understanding of Layer 7 load balancing.

---

### Task 4: DNS Management Using AWS Route 53

Leverage Amazon Route 53 to configure domain name registration, DNS routing, and health checks. Learn about record types, hosted zones, and how to direct traffic effectively across AWS regions and services.

---

### Task 5: Custom IAM Policy for EC2 Access Control

Design and apply custom IAM policies that restrict EC2 instance access based on specific actions, regions, or resource tags. This task emphasizes fine-grained permission control and least privilege security practices.

---

### Task 6: Cross-Account VPC Peering

Implement VPC peering between different AWS accounts to enable secure, private communication across VPCs. Understand peering connection setup, route table updates, and optional DNS resolution across accounts.

---

## Learning Objectives

By completing these tasks, you will:

- Gain hands-on experience with core AWS services  
- Automate infrastructure provisioning using best practices  
- Improve cloud security through IAM and networking controls  
- Understand real-world deployment architectures and traffic routing techniques  

---

## Prerequisites

- Basic understanding of AWS services such as EC2, VPC, IAM, and Load Balancers  
- Familiarity with the AWS Console and/or AWS CLI  
- (Optional) Knowledge of Terraform or CloudFormation  

---