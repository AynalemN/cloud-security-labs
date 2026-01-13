# LOGGING, SIEM & THREAT DETECTION (AWS)


Cloud Logging, SIEM Integration & Threat Detection on AWS

## Objective


Design and implement a centralized cloud logging and threat detection architecture in AWS to detect, alert, and respond to malicious activities such as unauthorized API calls, IAM privilege escalation, and suspicious login behavior.

This project demonstrates real-world detection engineering and incident analysis skills.

## Architecture Overview

- AWS CloudTrail for API activity logging

- Amazon CloudWatch for log aggregation and alerts

- AWS GuardDuty for threat detection

- Amazon OpenSearch for log analysis and visualization

## Tools & Technologies

- AWS CloudTrail

- AWS GuardDuty

- Amazon CloudWatch

- IAM

- AWS CLI

- OpenSearch

## Detection Scenarios Simulated
1️⃣ Unauthorized API Calls

- Simulated failed API calls using invalid credentials

- Detection via CloudTrail events and GuardDuty findings

2️⃣ IAM Privilege Escalation

- Created a low-privilege IAM user

- Attempted unauthorized role assumption

- GuardDuty and CloudTrail captured escalation attempts

3️⃣ Suspicious Login Activity

- Login attempts from unusual IP ranges

- Multiple failed authentication events

## Alerts & Monitoring

CloudWatch alarms configured for:

- Unauthorized API calls

- Root account usage

- IAM policy changes

- GuardDuty findings routed to CloudWatch

## Incident Timeline Example

- Event generated (suspicious API call)

- CloudTrail logs recorded

- GuardDuty flagged high-severity finding

- CloudWatch alert triggered

- Incident investigated and documented

## Evidence

- Screenshots of GuardDuty findings

- CloudWatch alarm triggers

- CloudTrail log entries

## security Best Practices Implemented

- MFA enabled for IAM users

- Least privilege IAM policies

- Centralized logging

- Continuous monitoring

## Outcome

- Improved cloud visibility

- Faster detection of malicious activity

- Demonstrated hands-on security monitoring experience
