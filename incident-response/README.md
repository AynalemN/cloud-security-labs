# Cloud Incident Response Playbook Using NIST Framework


## objective

Create a structured incident response (IR) playbook for cloud security incidents aligned with the NIST Incident Response Lifecycle.

This project demonstrates operational maturity and real incident handling capability, not just detection.

## Framework Used

NIST SP 800-61 Rev. 2

## Incident Response Phases
1️⃣ Detection & Analysis

- Alerts from GuardDuty and CloudWatch

- Log analysis using CloudTrail

- Incident severity classification

2️⃣ Containment

- Disable compromised IAM credentials

- Apply restrictive security group rules

- Block malicious IPs

3️⃣ Eradication

- Remove malicious IAM policies

- Rotate credentials

- Patch vulnerable resources

4️⃣ Recovery

- Restore services

- Validate system integrity

- Re-enable IAM access securely

5️⃣ Lessons Learned

- Root cause analysis

- Policy improvements

- Alert tuning recommendations

## Playbook Artifacts

- Incident classification matrix

- Response decision tree

- Escalation checklist

- Communication template

## Outcome

- Reduced Mean Time to Respond (MTTR)

- Repeatable and auditable response process

- Demonstrates senior-level security thinking

