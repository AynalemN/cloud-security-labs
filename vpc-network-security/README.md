# AWS VPC & Network Security Architecture
## Project Overview
This project demonstrates the design and implementation of a secure AWS Virtual Private Cloud (VPC) using network segmentation, least exposure, and defense-in-depth principles.
The goal is to minimize attack surface, control inbound/outbound traffic, and securely manage access to cloud resources.

## Skills Demonstrated
AWS VPC Design
Network Segmentation
Security Groups vs NACLs
Bastion Host Architecture
Private Subnet Isolation
Secure Internet Access via NAT
Cloud Network Threat Modeling

## Architecture Diagram
(Insert draw.io diagram here)
Components:
Custom VPC
Public Subnet
Private Subnet
Internet Gateway
NAT Gateway
Bastion Host
EC2 instances
Security Groups & NACLs

## Security Objectives
Prevent direct internet access to critical systems
Enforce least network exposure
Control east–west and north–south traffic
Enable secure administrative access
Reduce blast radius of compromises

## Network Architecture Design
1️⃣ Custom VPC
CIDR: 10.0.0.0/16
DNS hostnames enabled
No default VPC usage (security best practice)
Security Benefit:
Avoids insecure default configurations.

2️⃣ Subnet Segmentation
Subnet
Type
Purpose
Public Subnet
Public
Bastion Host
Private Subnet
Private
Application EC2

✔ Public-facing resources minimized
✔ Sensitive workloads isolated

3️⃣ Internet Gateway & NAT Gateway
Internet Gateway attached to VPC
NAT Gateway allows outbound-only internet access from private subnet
Security Benefit:
Private instances can update software without being exposed.

## Access Control Implementation
4️⃣ Bastion Host
Single hardened EC2 instance
SSH access restricted by IP
Key-based authentication only
### Why This Matters:
Prevents direct SSH access to private instances.

5️⃣ Security Groups (Primary Control)
Implemented stateful firewall rules:
Bastion SG
SSH (22) → Allowed from trusted IP only
Private EC2 SG
SSH allowed only from Bastion SG
No inbound internet access
✔ Least privilege
✔ Role-based traffic control

6️⃣ Network ACLs (Secondary Control)
Explicit deny rules for unused ports
Additional layer of protection
Design Choice:
Security Groups = main control
NACLs = coarse-grained boundary protection

⚠️ Threat Scenarios & Mitigations
Threat 1: Direct Internet Attack
Risk:
Publicly exposed EC2 targeted via brute force.
Mitigation:
No public IP on private EC2
Bastion-only access
IP-restricted SSH

Threat 2: Lateral Movement
Risk:
Compromised instance attacks internal resources.
Mitigation:
Subnet isolation
Security Group scoping
No open internal ports

Threat 3: Data Exfiltration
Risk:
Malicious outbound traffic.
Mitigation:
NAT Gateway only
Logging enabled (future integration with VPC Flow Logs)

## Validation & Testing

Verified no internet access to private EC2
Confirmed SSH access only via bastion
Tested blocked inbound traffic

## Lessons Learned
Default VPCs are insecure for production
Security Groups provide granular control
Bastion hosts significantly reduce attack surface

## Future Improvements
Add VPC Flow Logs
Integrate with CloudWatch alerts
Replace Bastion with AWS SSM Session Manager
Infrastructure as Code using Terraform

## References
AWS VPC Best Practices
AWS Well-Architected Framework – Security Pillar
NIST SP 800-53 (SC, AC controls)

## Author
Aynalem N.
Cloud Security Engineer
LinkedIn: www.linkedin.com/in/aynalemnigussie/ 

