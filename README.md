# AWS S3 Bucket Misconfiguration & Hardening

## Overview
This project simulates a real-world AWS S3 bucket misconfiguration that resulted in public data access. The bucket was intentionally misconfigured, exploited to confirm unauthorised access, and then secured using AWS security best practices.

The goal of this project is to demonstrate how common cloud storage misconfigurations can be identified, validated, and remediated using layered security controls.

---

## Misconfiguration
The S3 bucket was initially configured with public read access via a permissive bucket policy. Encryption at rest was not enabled, and access controls were insufficient, simulating a common cloud security vulnerability scenario.

---

## Exploitation
Public access was validated by attempting to retrieve objects from the bucket using unauthenticated requests. The test confirmed that objects could be accessed without authorisation, demonstrating risk of data exposure.

---

## Remediation
The bucket was secured through the following actions:
- Removed public bucket policies
- Enabled S3 Block Public Access
- Applied IAM least-privilege access using an EC2 role
- Enabled KMS encryption at rest
- Enabled CloudTrail logging for audit visibility

Policy examples used during remediation are documented in the `policies/` directory.

A step-by-step remediation checklist is provided in `remediation-checklist.md`.

---

## CloudTrail Logging & Verification
CloudTrail was configured with S3 data events to audit object-level access. After
accessing an object using the AWS CLI, the corresponding `GetObject` event was observed in the CloudTrail logs, confirming that S3 access was being recorded.

---

## Lessons Learned
This project highlights how easily cloud storage can be exposed through misconfiguration and reinforces the importance of defense-in-depth. Proper IAM access control, encryption, and logging are all required to effectively secure cloud storage services.

---

## Skills Developed
- Mitigating S3 bucket object exposure
- IAM and S3 resource policy hardening
- Implementing encryption at rest with AWS KMS
- Auditing and monitoring access using CloudTrail
