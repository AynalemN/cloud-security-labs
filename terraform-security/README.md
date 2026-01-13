# Secure AWS Infrastructure Deployment Using Terraform

## Objective

Deploy AWS infrastructure using Infrastructure as Code (IaC) with secure-by-default configurations, demonstrating automation and DevSecOps awareness.

## Tools & Technologies

- Terraform

- AWS Provider

- IAM

- VPC

- Security Groups

## Infrastructure Deployed

- VPC with private and public subnets

- Secure security groups (least privilege)

- IAM roles with restricted permissions

- Logging enabled by default

## Security Best Practices

- No hardcoded credentials

- IAM roles instead of users

- Minimal inbound access

- Resource tagging for auditability

## Terraform Structure

- main.tf — core resources

- variables.tf — reusable inputs

- outputs.tf — exposed values

## Outcome

- Repeatable and auditable infrastructure

- Reduced configuration drift

- Foundation for DevSecOps pipelines
