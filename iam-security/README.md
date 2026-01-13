# AWS IAM Security Hardening & Least Privilege Implementation #
 ## Project OvervieW

This project demonstrates the design, implementation, and validation of secure AWS Identity and Access Management (IAM) following least privilege, defense in depth, and zero trust principles.

The goal is to prevent unauthorized access, reduce blast radius, and detect misconfigurations commonly exploited in cloud environments. 
 
## Skills Demonstrated ##
 -AWS IAM(Users,Roles,Policies)
 -Least Privilege Access Design
 -IAM Access Analyzer
 -MFA Enforcement
 -Credential Rotation
 -Threat Modeling
 -Secirity Documentation

 ## Architecture Diagram ## 
  Components: 

 -IAM Users (Admin, Developer, ReadOnly)
 -IAM Roles (EC2 Role, Lambda Role)
 -AWS Services (EC2, S3)
 -IAM Acess Analyzer
 -MFA Device

## Security Objectives

-Eliminate long-term credentials where possible
-Enforce least privilege using role-based access
-Detect overly permissive IAM policies
-Prevent privilege escalation
-Improve visibility into IAM risks

## IAM Design & Implementation
1️⃣ IAM Users & Roles

Created the following IAM identities:

Identity	Purpose	Access Type
AdminUser	Account administration	Role-based
DevUser	Application development	Least privilege
ReadOnlyUser	Auditing & monitoring	Read-only
EC2Role	EC2 instance access	Temporary credentials

Key Design Decision:
Roles are preferred over users for AWS service access to avoid long-term credentials.

2️⃣ Least Privilege IAM Policies

Implemented custom IAM policies instead of AWS managed policies.

Example:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::secure-bucket/*"
    }
  ]
}


✔ No wildcard permissions
✔ Scoped to specific resources
✔ Explicit deny where applicable

3️⃣ MFA Enforcement

Enabled MFA for all IAM users

Enforced MFA using IAM policy conditions

Tested access denial without MFA

Security Benefit:
Prevents account takeover even if credentials are compromised.

4️⃣ IAM Access Analyzer

Enabled IAM Access Analyzer to:

Detect public or cross-account access

Identify overly permissive policies

Review findings and remediate risks

Finding Example:

Policy allowing s3:* on all resources

Fixed by scoping permissions to a single bucket

5️⃣ Credential Rotation

Removed unused access keys

Rotated active keys

Verified access after rotation

### Best Practice:
No permanent credentials for services. Roles only.

## ⚠️ Threat Scenarios & Mitigation
### Threat 1: Over-Privileged User

Risk:
Developer with AdministratorAccess can escalate privileges.

### Mitigation:

Removed managed admin policy

Applied custom least-privilege policy

Monitored via Access Analyzer

### Threat 2: Credential Compromise

Risk:
Stolen access key used from external IP.

Mitigation:

MFA enforcement

Short-lived role credentials

Access key rotation

### Threat 3: Public Resource Exposure

Risk:
S3 bucket accidentally exposed.

Mitigation:

Resource-level policies

IAM Access Analyzer

Explicit deny statements

## Security Validation

Tested access denial scenarios

Verified IAM policy boundaries

Confirmed alerts from Access Analyzer

## Lessons Learned

AWS managed policies are often too permissive

IAM roles dramatically reduce credential risk

Continuous monitoring is critical in cloud environments

## Future Improvements

Integrate CloudTrail log analysis

Automate IAM deployment using Terraform

Add GuardDuty alerting for IAM abuse

## References

AWS IAM Best Practices

NIST SP 800-53 (AC, IA controls)

AWS Well-Architected Security Pillar

## 👤 Author

Aynalem Nigussie
Cloud Security Engineer
https://www.linkedin.com/in/aynalemnigussie/
