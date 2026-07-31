# AWS Highly Available, Load-Balanced VPC Architecture

## What I Built
I built a multi-AZ web architecture on AWS to practice real-world cloud networking, traffic management, and fault tolerance. The goal was to build a setup where backend web servers live safely in private subnets, incoming traffic is handled by a Load Balancer, and the infrastructure automatically replaces any server that fails without breaking the application.

## Architecture Diagram **(created using draw.io)**
> **![Diagram](https://github.com/danyshrf/AWS-High-Availability/blob/main/Screenshots(proofs)/photo_draw.io.jpg)**

## 🛠️ Technologies & AWS Services Used
* **Amazon VPC:** Split into public and private subnets across 2 Availability Zones.
* **EC2 Auto Scaling Groups (ASG):** Keeps two web servers running and replaces them if they crash.
* **Application Load Balancer (ALB):** Routes incoming web traffic to healthy backend servers.
* **Security Groups:** Firewall rules set up so servers only accept traffic from the load balancer.
* **NAT Gateway:** Lets private EC2 instances access the internet for software updates without exposing them to incoming internet connections.
