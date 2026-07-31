# AWS Highly Available, Load-Balanced VPC Architecture

## What I Built
I built a multi-AZ web architecture on AWS to practice real-world cloud networking, traffic management, and fault tolerance. The goal was to build a setup where backend web servers live safely in private subnets, incoming traffic is handled by a Load Balancer, and the infrastructure automatically replaces any server that fails without breaking the application.

## Architecture Diagram **(created using draw.io)**
> **![Diagram](https://github.com/danyshrf/AWS-High-Availability/blob/main/Screenshots(proofs)/photo_draw.io.jpg)**

## AWS Services Used
* **Amazon VPC:** Split into public and private subnets across 2 Availability Zones.
* **EC2 Auto Scaling Groups (ASG):** Keeps two web servers running and replaces them if they crash.
* **Application Load Balancer (ALB):** Routes incoming web traffic to healthy backend servers.
* **Security Groups:** Firewall rules set up so servers only accept traffic from the load balancer.
* **NAT Gateway:** Lets private EC2 instances access the internet for software updates without exposing them to incoming internet connections.

## Security & Traffic Flow 
1. **ALB Security Group(Public):** Open to `0.0.0.0/0` on Port 80 (HTTP) to accept global internet traffic.
2. **EC2 (Web Server) Security Group(Private):** Hidden in private subnets. Their security group drops all incoming traffic unless it comes directly from the Load Balancer's Security Group ID.
* **This setup prevents anyone from bypassing the load balancer or accessing the EC2 instances directly from the outside.

## Testing & Verification
1. **Target Group Health Checks
* After launching the instances, the Load Balancer ran health checks and confirmed that both EC2 instances were Healthy across both Availability Zones.
> * > **![Before](https://github.com/danyshrf/AWS-High-Availability/blob/main/Screenshots(proofs)/photo_draw.io.jpg)**
