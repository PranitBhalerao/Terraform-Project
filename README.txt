Overview

This project is built using Terraform to automate infrastructure provisioning. It sets up a secure and scalable environment with AWS resources, including networking, security, compute, and load balancing.

Prerequisites

Before running this project, ensure you have the following installed:

Terraform

AWS CLI (if deploying to AWS) or respective cloud provider CLI

Proper access credentials configured (e.g., AWS IAM user with appropriate permissions)

Resources Used

This project provisions the following AWS resources:

VPC: Creates a Virtual Private Cloud (VPC) for networking.

Subnets: Two subnets in different availability zones for high availability.

Internet Gateway: Allows internet access to the VPC.

Route Table & Associations: Configures routing to allow public internet access.

Security Group: Defines firewall rules to manage inbound and outbound traffic.

S3 Bucket: Creates an AWS S3 bucket for storage (currently commented out for public access control).

EC2 Instances: Two web servers running on AWS EC2.

Application Load Balancer (ALB): Distributes traffic between the web servers.

Target Group & Attachments: Registers EC2 instances to the ALB for traffic routing.

ALB Listener: Listens for HTTP traffic and forwards requests to the target group.

Project Structure

Terraform-Project/
│── main.tf          # Main Terraform configuration file
│── variables.tf     # Variables used in the configuration
│── outputs.tf       # Outputs generated after deployment
│── provider.tf      # Cloud provider configuration
│── modules/         # Optional Terraform modules
│── userdata.sh      # Startup script for EC2 instances
│── README.md        # Project documentation

Usage

Initialize Terraform

terraform init

Plan the deployment

terraform plan

Apply the configuration

terraform apply -auto-approve

Destroy resources (if needed)

terraform destroy -auto-approve

Best Practices

Use remote state management with Terraform Cloud or AWS S3 + DynamoDB.

Define variables in variables.tf and avoid hardcoding values.

Implement proper security measures (e.g., IAM policies, secrets management).

Regularly review security groups and access control lists.

Outputs

Load Balancer DNS: After deployment, you can access your application via the following DNS:

output "loadbalancerdns" {
  value = aws_lb.myalb.dns_name
}

Contributing

Contributions are welcome! Feel free to submit issues or pull requests.

License

This project is licensed under the MIT License. See LICENSE for details.