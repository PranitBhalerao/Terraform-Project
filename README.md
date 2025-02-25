﻿# Terraform-Project

## Overview
This project leverages Terraform to automate infrastructure provisioning on AWS. It sets up a secure and scalable environment with various AWS resources, including networking, security, compute, and load balancing.

## Prerequisites
Before running this project, ensure you have the following installed:

- **Terraform**: Install from [Terraform's official site](https://developer.hashicorp.com/terraform/downloads).
- **AWS CLI**: Required for deploying to AWS. Install from [AWS CLI installation guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).
- **AWS Access Credentials**: Configure with an IAM user that has the necessary permissions.

## Resources Provisioned
This project provisions the following AWS resources:

- **VPC**: Creates a Virtual Private Cloud (VPC) for networking.
- **Subnets**: Two subnets across different availability zones for high availability.
- **Internet Gateway**: Enables internet access for the VPC.
- **Route Table & Associations**: Configures routing for internet access.
- **Security Group**: Defines firewall rules to manage inbound and outbound traffic.
- **S3 Bucket**: (Optional) Creates an AWS S3 bucket for storage (currently commented out for security reasons).
- **EC2 Instances**: Two web servers running on AWS EC2.
- **Application Load Balancer (ALB)**: Distributes traffic between web servers.
- **Target Group & Attachments**: Registers EC2 instances to the ALB.
- **ALB Listener**: Listens for HTTP traffic and forwards requests to the target group.

## Project Structure
```
Terraform-Project/
│── main.tf          # Main Terraform configuration file
│── variables.tf     # Variables used in the configuration
│── outputs.tf       # Outputs generated after deployment
│── provider.tf      # Cloud provider configuration
│── modules/         # Optional Terraform modules
│── userdata.sh      # Startup script for EC2 instances
│── README.md        # Project documentation
```

## Usage
### Initialize Terraform
```sh
terraform init
```

### Plan the Deployment
```sh
terraform plan
```

### Apply the Configuration
```sh
terraform apply -auto-approve
```

### Destroy Resources (if needed)
```sh
terraform destroy -auto-approve
```

## Best Practices
- Use **remote state management** with Terraform Cloud or AWS S3 + DynamoDB.
- Define variables in `variables.tf` to avoid hardcoding values.
- Implement proper security measures (e.g., IAM policies, secrets management).
- Regularly review **security groups** and **access control lists**.

## Outputs
After deployment, you can access your application via the following Load Balancer DNS:
```hcl
output "loadbalancerdns" {
  value = aws_lb.myalb.dns_name
}
```


