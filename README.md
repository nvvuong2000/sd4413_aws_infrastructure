# Terraform AWS

This repository contains Terraform configuration files for deploying infrastructure on AWS, including VPC, subnets, EKS cluster, and ECR repositories.

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) (v1.x or later)
- AWS account with appropriate permissions

## Configuration

### Variables

The following variables need to be configured in your `terraform.tfvars` file or via environment variables:

- `vnet_cidr_block`: The CIDR block for the VPC.
- `vpc_tags`: Tags for the VPC.
- `public_subnet_cidr`: CIDR blocks for public subnets.
- `private_subnet_cidr`: CIDR blocks for private subnets.
- `subnet_azs`: Availability zones for subnets.
- `public_subnet_tags`: Tags for public subnets.
- `private_subnet_tags`: Tags for private subnets.
- `eks_cluster_name`: Name of the EKS cluster.
- `eks_public_access_cidrs`: CIDR blocks that can access the EKS API server.

### Example `terraform.tfvars`

```hcl
vnet_cidr_block = "10.0.0.0/16"
vpc_tags = {
  Name = "my-vpc"
}
public_subnet_cidr = ["10.0.1.0/24", "10.0.2.0/24"]
private_subnet_cidr = ["10.0.3.0/24", "10.0.4.0/24"]
subnet_azs = ["ap-southeast-1a", "ap-southeast-1b"]
public_subnet_tags = {
  Name = "public-subnet"
}
private_subnet_tags = {
  Name = "private-subnet"
}
eks_cluster_name = "my-eks-cluster"
eks_public_access_cidrs = ["0.0.0.0/0"]