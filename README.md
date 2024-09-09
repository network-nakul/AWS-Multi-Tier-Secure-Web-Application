# AWS Project: Secure Multi-Tier Web Application Deployment

## Overview
This project demonstrates the deployment and configuration of a secure multi-tier web application on AWS, ensuring scalability, security, and high availability. The project was carried out as part of a competition focusing on designing and configuring Virtual Private Cloud (VPC) architecture with various AWS services.

## Services Used
- **Amazon VPC**: Configured for secure networking with public and private subnets.
- **Amazon EC2**: Launched instances for web servers and database.
- **Amazon RDS**: Deployed MySQL database in a private subnet.
- **Amazon Application Load Balancer (ALB)**: Used for traffic distribution across multiple web servers.
- **AWS Auto Scaling**: Implemented for scaling web servers based on traffic.
- **AWS Security Groups and NACLs**: Configured for access control and security.
- **AWS Internet Gateway & NAT Gateway**: Set up for internet connectivity and routing.

## Project Architecture
The architecture consists of a VPC with multiple subnets distributed across different availability zones for high availability:
- **Public Subnet**: For web servers.
- **Private Subnet**: For the database server.
- **Internet Gateway**: To allow outbound internet access for instances in the public subnet.
- **NAT Gateway**: Used for secure outbound internet access for the private subnet.

### VPC and Subnets
- VPC CIDR: `10.0.0.0/16`
- Public Subnet: `10.0.1.0/24` (For web servers)
- Private Subnet: `10.0.2.0/24` (For database servers)
- Subnets distributed across multiple Availability Zones for high availability.

### Security Configuration
- **Web Server Security Group**: Allows HTTP (port 80) and SSH (port 22) traffic from the internet.
- **Database Security Group**: Allows MySQL (port 3306) traffic only from instances in the private subnet.

### Network ACLs
- Public Subnet NACL: Allows HTTP (80) and SSH (22) traffic.
- Private Subnet NACL: Allows MySQL traffic from the public subnet.

## Steps Taken
1. **VPC and Subnet Setup**:
   - Created a VPC with the CIDR block `10.0.0.0/16`.
   - Set up a public subnet for web servers and a private subnet for database servers across different availability zones for high availability.

2. **Security Configuration**:
   - Configured security groups for the web servers and database with appropriate inbound/outbound rules.
   - Set up Network ACLs to further control traffic between the subnets.

3. **Internet Connectivity**:
   - Attached an Internet Gateway to the VPC for internet access.
   - Configured route tables to route traffic from the public subnet to the Internet Gateway and private subnet traffic through a NAT Gateway.

4. **Application Deployment**:
   - Launched EC2 instances in the public subnet for the web server and RDS instance in the private subnet for the database.
   - Set up an Application Load Balancer (ALB) to distribute incoming traffic across web servers.
   - Configured Auto Scaling for web servers to handle varying levels of traffic.

## Challenges Faced
- Configuring the security groups and NACLs to balance security and functionality.
- Ensuring high availability by distributing resources across multiple availability zones.

## Future Improvements
- Implement a WAF (Web Application Firewall) for better security.
- Configure automated backups and database failover for the RDS instance.
- Add monitoring and alerting using AWS CloudWatch.

## How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/YourUsername/AWS-Project.git
