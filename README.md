
# AWS PrivateLink: Secure VPC-to-VPC Application Access

## Overview
This project demonstrates how to use AWS PrivateLink to enable private communication between two VPCs — a Provider VPC hosting a web application and a Customer VPC that consumes the service — without exposing traffic to the public internet.

## Architecture Summary

- **Provider VPC CIDR**: 10.0.0.0/16
  - Private Subnet: 10.0.2.0/24
  - Hosted application on EC2 instance (port 80)
  - Created a **Target Group** and **Network Load Balancer (NLB)**
  - Exposed application via **AWS PrivateLink Endpoint Service**

- **Customer VPC CIDR**: 192.168.0.0/16
  - Private Subnet: 192.168.2.0/24
  - Created **Interface Endpoint** to connect to the Provider’s service
  - Verified connectivity using `curl` to the PrivateLink DNS name

## Components Deployed

- **EC2 Instances**: 
  - Provider EC2 (Apache Web Server)
  - Customer EC2 (Client machine to access the service)
- **Network Load Balancer**: Forwarding traffic on port 80 to the target EC2
- **Target Group**: Associated with the EC2 instance in the Provider VPC
- **PrivateLink Endpoint Service**: Exposed through the NLB
- **Interface Endpoint**: Created in the Customer VPC to connect to the service

## Verification
The project was verified by SSH-ing into the private EC2 instance in the Customer VPC and running:
```bash
curl <PrivateLink_DNS_Name>
```
This returned the expected response from the Apache web server in the Provider VPC.

## Built With
- AWS Console (GUI-based deployment)
- EC2, VPC, PrivateLink, NLB, Target Groups, Security Groups

---

## Author

Mohaned Mohamed  
Glasgow, United Kingdom  
m.gorashi282@gmail.com | +447417414418  
[LinkedIn Profile](https://www.linkedin.com) | [GitHub Profile](https://www.github.com)
