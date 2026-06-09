# Secure Three-Tier AWS Architecture

> AWS Region: ap-south-1 (Mumbai) | VPC: 10.0.0.0/16

## Architecture Overview

<img width="1536" height="1024" alt="finallll archuuuu" src="https://github.com/user-attachments/assets/3c601606-a8f9-4930-b560-2cb7d59f4a94" />


## What This Project Does

Implements a production-grade, high-availability three-tier web 
architecture on AWS with automated security auditing.

- **Presentation tier** — Application Load Balancer across 2 AZs
- **Application tier** — Auto Scaling EC2 in private subnets
- **Data tier** — RDS MySQL with Multi-AZ in isolated subnets
- **Security auditing** — Prowler scanning against CIS benchmarks
- **Secure report delivery** — Private S3 + CloudFront (HTTPS)

## Architecture Decisions Worth Noting --

| Decision | Why |
|---|---|
| NAT Instance over NAT Gateway | Cost optimisation for project scope |
| S3 Block Public Access ON | Report never exposed to open internet |
| CloudFront OAC | Only authorised distribution reads from S3 |
| Isolated subnets for RDS | Zero internet path to the database |
| Bastion Host | No direct SSH to private EC2s |

## Security Audit Results (Prowler)

<img width="1878" height="972" alt="Screenshot from 2026-05-28 00-38-26" src="https://github.com/user-attachments/assets/03d01d5f-d175-4399-9eb4-438de6d6cab6" />


<img width="1865" height="976" alt="Screenshot from 2026-05-28 00-38-07" src="https://github.com/user-attachments/assets/872d5161-5943-4399-83f3-d0bd71c34092" />


<img width="1869" height="971" alt="Screenshot from 2026-05-27 23-51-52" src="https://github.com/user-attachments/assets/f5128e52-64f2-4732-84bf-4a67d9cfe01b" />

## Infrastructure Screenshots

[Prowler IAM Role Screenshot]

<img width="1882" height="976" alt="Screenshot from 2026-05-28 01-00-20" src="https://github.com/user-attachments/assets/ae3a3bbb-8ec4-425c-bbf1-5eed44ab1e28" />

[Instances Screenshot]

<img width="1879" height="974" alt="Screenshot from 2026-05-28 00-45-09" src="https://github.com/user-attachments/assets/c3201f24-862e-44de-ac5f-110feb3c9f3b" />

[Auto Scaling Screenshot]

<img width="1877" height="977" alt="Screenshot from 2026-05-28 00-45-43" src="https://github.com/user-attachments/assets/fa000402-7204-4994-88ce-169c0e600d2f" />

[Target Groups Screenshot]

<img width="1878" height="975" alt="Screenshot from 2026-05-28 00-45-59" src="https://github.com/user-attachments/assets/2ea21565-3289-4ed5-9488-ccf0aaebe7b1" />

[Load Balancer Screenshot]

<img width="1877" height="974" alt="Screenshot from 2026-05-28 00-47-24" src="https://github.com/user-attachments/assets/9c9a7411-e08b-4760-80a9-8a3e4c0bebbd" />

<img width="1880" height="977" alt="Screenshot from 2026-05-28 00-48-43" src="https://github.com/user-attachments/assets/54a0fd59-6a2b-421c-b903-b98476430127" />


### VPC and Networking

[VPC screenshot]

<img width="1879" height="973" alt="Screenshot from 2026-05-28 00-43-14" src="https://github.com/user-attachments/assets/6baef6d8-e35b-4ce2-a9f9-a85b503e3a0b" />

[subnet screenshot] 

<img width="1881" height="972" alt="Screenshot from 2026-05-28 00-43-40" src="https://github.com/user-attachments/assets/fbd86d0a-b61a-45c6-a231-0e3a3537d6e9" />

[route table screenshot]

<img width="1880" height="974" alt="Screenshot from 2026-05-28 00-43-49" src="https://github.com/user-attachments/assets/cb9714e3-3102-4503-9010-6ab59a8785a2" />

[Internet Gateway screenshot]

<img width="1877" height="975" alt="Screenshot from 2026-05-28 00-43-59" src="https://github.com/user-attachments/assets/270c3172-7703-4c3a-b6d9-78de88d05704" />

[Security Groups screenshot]

<img width="1878" height="976" alt="Screenshot from 2026-05-28 00-44-17" src="https://github.com/user-attachments/assets/5d039165-12e3-498e-b9fd-36ddb774d746" />


### Application Layer — Healthy Targets

<img width="1880" height="977" alt="Screenshot from 2026-05-28 00-48-43" src="https://github.com/user-attachments/assets/4a8dbf3f-f08c-41f6-86e9-36d4ddac8a5a" />

<img width="1881" height="1010" alt="Screenshot from 2026-05-28 00-48-29" src="https://github.com/user-attachments/assets/c1847735-6f93-476d-9c5f-031a92c7f9b1" />

### Database — Multi-AZ, No Public Access

<img width="1874" height="972" alt="Screenshot from 2026-05-28 00-58-50" src="https://github.com/user-attachments/assets/6bfa04a3-fe04-4063-9f3b-c2868f6e2690" />

<img width="1880" height="975" alt="Screenshot from 2026-05-28 00-59-06" src="https://github.com/user-attachments/assets/b7d315da-4627-4ada-bd02-f12aff03bcce" />

<img width="1878" height="972" alt="Screenshot from 2026-05-28 00-59-20" src="https://github.com/user-attachments/assets/ad31d1d1-3508-4ccc-802f-6eb0e50bea3a" />

### Report Delivery — Private S3 + CloudFront

[S3 block public access screenshot]

<img width="1883" height="973" alt="Screenshot from 2026-05-28 00-54-20" src="https://github.com/user-attachments/assets/6ebb9d93-6bb8-4465-b39c-d9d22761be92" />

<img width="1877" height="971" alt="Screenshot from 2026-05-28 00-54-35" src="https://github.com/user-attachments/assets/2cb6aba0-46ec-417d-8445-e06ba3d01392" />

[CloudFront distribution screenshot]

<img width="1880" height="976" alt="Screenshot from 2026-05-28 00-57-03" src="https://github.com/user-attachments/assets/650f0aaa-d52b-4cc4-9506-4a200b721d1c" />


## Tech Stack

AWS VPC · EC2 · ALB · Auto Scaling · RDS MySQL · 
S3 · CloudFront · IAM · Prowler · Python Flask
