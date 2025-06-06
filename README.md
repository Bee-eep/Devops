# Terraform AWS Infrastructure Deployment

This repository contains Terraform configurations to provision and manage AWS infrastructure. The project is divided into phases, starting from a basic EC2 instance creation and evolving into a modular, multi-environment setup.

---

## Table of Contents

- [Phase 1: Basic EC2 Instance Creation](#phase-1-basic-ec2-instance-creation-april-1-2025)
- [Phase 2: Modularization](#phase-2-modularization-april-4-2025)
- [Phase 3: Multi-Environment Deployment](#phase-3-multi-environment-deployment-april-10-2025)
- [Terraform Workflow](#terraform-workflow)
- [Usage](#usage)

---

## Phase 1: Basic EC2 Instance Creation (April 1, 2025)

This initial phase focuses on setting up the necessary tools and creating a single EC2 instance with specific configurations.

### Prerequisites

1.  **Install Terraform**: Download and install Terraform from the official website.
2.  **Install AWS CLI**: Download and install the AWS Command Line Interface.
3.  **Configure AWS CLI**: Configure the AWS CLI with your Access Key and Secret Key by running `aws configure`.

### Configuration Steps

1.  **Provider Configuration (`provider.tf`)**: This file configures the AWS provider, specifying the region where the resources will be created.

2.  **Main Configuration (`main.tf`)**: This file contains the resource block for the EC2 instance. The configuration was adapted from the official Terraform AWS documentation to meet the following requirements:
    * **AMI ID**: A specific Ubuntu AMI ID is used.
    * **Instance Type**: The instance type is set to `t3.micro`.
    * **Subnet ID**: The Subnet ID is manually provided.
    * **Public IP**: The public IP address is disabled.
    * **EBS Volume**: The root EBS volume size is increased from the default 8 GB to 12 GB.

3.  **Variable Declaration (`variables.tf`)**: To make the configuration reusable, all hardcoded values from `main.tf` were declared as variables in this file.

4.  **Variable Definitions (`terraform.tfvars`)**: The values for the variables declared in `variables.tf` are defined in this file. This allows for easy modification of instance details without altering the core configuration files.

---

## Phase 2: Modularization (April 4, 2025)

The focus of this phase was to refactor the configuration into a modular structure for better organization, reusability, and scalability.

### Module Structure

The infrastructure is broken down into reusable modules for:
* **VPC**: Manages the Virtual Private Cloud.
* **Subnet**: Manages the subnets within the VPC.
* **EC2**: Manages the EC2 instance.

### Child Module Implementation

* **Variable Declaration**: Each module has its own `variables.tf` to define the input values it requires.
* **Resource Blocks**: The resource blocks within each module are defined with the maximum number of configurable arguments to ensure flexibility.
* **Output Declarations (`outputs.tf`)**: Each module declares necessary attributes as outputs (e.g., VPC ID, Subnet ID). This allows other modules to use these values.

### Root Module Implementation

* **`main.tf`**: The root `main.tf` file now calls the created modules (VPC, Subnet, and EC2) to provision the infrastructure. It is responsible for passing the necessary variable values to the child modules. The EC2 instance is specifically configured to be launched within the subnet created by the subnet module.
* **`variables.tf`**: The root module's `variables.tf` defines the variables that will be passed down to the child modules.
* **`terraform.tfvars`**: This file in the root directory provides the actual values for the variables, which are then propagated to the respective modules.

---

## Phase 3: Multi-Environment Deployment (April 10, 2025)

This phase expands the project to support three distinct environments (e.g., local, dev, prod) with backend configurations and a more comprehensive set of resources.

### Environment Configuration

Each environment has its own backend configuration to store the Terraform state file separately. This is crucial for preventing state conflicts between environments.

### Managed Resources

The Terraform configuration manages the following AWS resources for each environment:

* **VPC**: A dedicated Virtual Private Cloud.
* **Subnet**: Subnets within the VPC.
* **EIP**: Elastic IP addresses for stable public IPs.
* **S3**: S3 buckets for object storage.
* **EC2**: Compute instances.
* **Security Groups**: Firewall rules to control inbound and outbound traffic.
* **Internet Gateway (IGW)**: To provide internet access to the VPC.
* **NAT Gateway**: To allow instances in private subnets to access the internet.

The configuration leverages Terraform functions for dynamic values and outputs to expose important resource attributes.

---

## Terraform Workflow

### Creating New Resources

This is the standard workflow for creating and managing resources that are defined in the Terraform configuration files.

```bash
# Write The config/code -> Terraform Apply -> State file updated by terraform -> Cloud resource will be managed via terraform -> Update / Make Changes to the config
