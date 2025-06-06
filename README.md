Terraform AWS Infrastructure Project
This repository contains Terraform configurations to build, manage, and scale AWS infrastructure. The project is structured to support multiple environments and reusable components through modules, demonstrating a production-grade approach to Infrastructure as Code (IaC).

Table of Contents
Project Overview

Prerequisites

Configuration

AWS Credentials

Directory Structure

Usage and Workflows

Initializing the Backend

Deploying Infrastructure

Passing Variables

Destroying Infrastructure

Advanced Workflows

Targeting Specific Resources

Importing Existing Resources

Architectural Concepts

Modularization

Environments

State Management

Outputs

Project Overview
This project automates the provisioning of core AWS services. It is designed to be version-controlled and deployed through a CI/CD pipeline. The configurations evolve from a single EC2 instance to a multi-environment, modular architecture.

The managed resources include:

VPC, Subnets (Public and Private)

Internet Gateway (IGW)

NAT Gateway

Elastic IP (EIP)

Security Groups

EC2 Instances

S3 Buckets

IAM Roles and Policies (Implicit)

Prerequisites
Before you begin, ensure you have the following tools installed on your local machine:

Terraform: Download and Install Terraform

AWS CLI: Install and Configure the AWS CLI

Configuration
AWS Credentials
The Terraform AWS provider requires credentials to manage your resources. Configure your AWS CLI with an Access Key and Secret Key by running:

aws configure

Terraform will automatically use these credentials. It is best practice to use an IAM role with the minimum required permissions.

Directory Structure
The project is organized into modules for reusable components and environments for isolated deployments (e.g., dev, staging, production).

.
├── environments/
│   ├── dev/
│   │   ├── backend.tf      # S3 backend configuration for dev state
│   │   ├── main.tf         # Root module instantiation for dev
│   │   ├── outputs.tf      # Root outputs for dev
│   │   ├── terraform.tfvars  # Variable values for dev
│   │   └── variables.tf    # Variable declarations for dev
│   ├── staging/
│   │   └── ...             # Staging environment configuration
│   └── prod/
│       └── ...             # Production environment configuration
│
├── modules/
│   ├── vpc/
│   │   ├── main.tf
│   │   ├── outputs.tf
│   │   └── variables.tf
│   ├── ec2/
│   │   └── ...
│   ├── s3/
│   │   └── ...
│   └── security_group/
│       └── ...
│
└── README.md

Usage and Workflows
All Terraform commands should be run from within a specific environment's directory (e.g., environments/dev/).

Initializing the Backend
The first command you must run is terraform init. This will download the necessary provider plugins and configure the remote backend as defined in backend.tf.

cd environments/dev/
terraform init

Deploying Infrastructure
Plan: Review the changes Terraform will make to your infrastructure. This is a dry run and is highly recommended.

terraform plan -var-file="terraform.tfvars"

Apply: Provision the resources as defined in the configuration files.

terraform apply -var-file="terraform.tfvars"

Passing Variables
While terraform.tfvars is the primary method for setting values, you can also pass variables directly on the command line. This is useful for sensitive data or for use in automated scripts.

terraform plan -var="windows_password=SomeSecurePassword@123"

Destroying Infrastructure
To tear down all resources managed by the configuration in the current environment, use the destroy command.

terraform destroy

Advanced Workflows
Targeting Specific Resources
In some cases, you may need to apply changes to a single resource without affecting the rest of the stack. Use the -target flag with caution, as it can cause state drift.

Example: Apply changes only to the S3 module.

terraform apply -target="module.s3_import"

Importing Existing Resources
If a resource was created manually in the AWS Console, you can bring it under Terraform's management using the import command.

Write the Configuration: First, write the resource block in your .tf files for the resource you want to import.

Run Import: Use the terraform import command, providing the resource address and the cloud identifier.

Example: Import an existing S3 bucket.

# The resource block 'aws_s3_bucket.tfstate' must exist within the 's3_import' module
terraform import module.s3_import.aws_s3_bucket.tfstate arn:aws:s3:::s3bucketbennttnoida

Architectural Concepts
Modularization
This project heavily utilizes Terraform Modules to create logical abstractions and promote code reuse. Each core component (VPC, EC2, S3) is defined in its own module with a clear interface using input variables and outputs. The root module in each environment then composes these modules to build the final infrastructure.

Environments
To ensure separation and prevent conflicts, each deployment environment (dev, staging, prod) has its own directory. This allows for:

Separate State Files: Each environment maintains its own state, preventing changes in dev from accidentally impacting prod.

Configuration Differences: Each environment has its own terraform.tfvars file to specify different instance sizes, network ranges, or feature flags.

State Management
Terraform state is stored remotely in an AWS S3 bucket with state locking enabled via DynamoDB. This is configured in the backend.tf file and is critical for team collaboration, preventing concurrent state file corruption.

Outputs
Module outputs are used to expose key information about created resources (e.g., a VPC's ID, an EC2 instance's public IP). The root module consumes these outputs to pass data between modules and also declares its own outputs to display important values to the user after an apply is complete.
