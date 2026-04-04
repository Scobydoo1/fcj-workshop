---
title: "Week 2 Worklog"
date: 2026-01-12
weight: 2
chapter: false
pre: "<b>1.2. </b>"
---

# ☁️ AWS Training Worklog: Week 2 - Networking & Compute Basics

**Status:** 🟢 Completed  
**Timeframe:** 12/01/2025 - 18/01/2025  
**Objective:** Design a custom cloud network architecture and deploy scalable virtual servers to host applications.

This document tracks my Week 2 progress. Having secured the account in Week 1, this week focuses on provisioning the core network topology and compute resources required for application deployment.

---

## 📅 Daily Task Log

### Module 2.1: Network Infrastructure (Amazon VPC)
* **Date Completed:** 13/01/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Created a custom Virtual Private Cloud (VPC) from scratch.
- [x] Configured Public and Private Subnets across two Availability Zones for high availability.
- [x] Deployed an Internet Gateway (IGW) and configured Route Tables for public subnet routing.
- [x] Set up a NAT Gateway to allow private subnets to download updates securely.

**Notes & Observations:**
> Carefully architecting the public/private subnet split is crucial here. The goal is to eventually host user-facing React frontends in the public subnets (or via CloudFront later), while keeping the Java Spring Boot backend services securely isolated in the private subnets.

**Artifacts:**
- 🖼️ `[vpc-resource-map-20250113.png]`

---

### Module 2.2: Compute Cloud Basics (Amazon EC2)
* **Date Completed:** 15/01/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Provisioned an Amazon EC2 instance (Ubuntu 24.04 LTS) using the Free Tier `t2.micro` family.
- [x] Generated and securely downloaded a `.pem` SSH key pair.
- [x] Configured Security Groups to allow inbound SSH (Port 22) from my specific IP and HTTP (Port 80) from anywhere.
- [x] Assigned an Elastic IP to the instance to maintain a static public IPv4 address across reboots.

**Troubleshooting / Learnings:**
> Initially encountered a connection timeout when trying to SSH. Realized the Security Group was tied to the default VPC instead of the custom VPC created in Module 2.1. Corrected the association and successfully established the SSH session.

---

### Module 2.3: IAM Roles for EC2 & AWS CLI
* **Date Completed:** 17/01/2025
* **Time Spent:** 2.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Created an IAM Role with read-only access to specific AWS services.
- [x] Attached the IAM Role directly to the running EC2 instance via the console.
- [x] SSH'd into the instance and installed/configured the AWS CLI.
- [x] Executed AWS CLI commands from the instance to verify permissions without hardcoding any access keys.

**Notes & Observations:**
> Attaching IAM roles directly to compute instances is a great security practice. It ensures that when we eventually deploy background workers or logging agents they can securely stream data to AWS services without exposing credentials in the codebase.

**Artifacts:**
- 📄 `[ec2-trust-policy.json]`
- 💻 `[cli-output-sts-get-caller-identity.txt]`

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully built a secure, custom network topology and deployed a functional Linux server inside it, fully accessible via SSH.
* **Concepts to review later:** Need to look deeper into VPC Flow Logs to understand network traffic monitoring, which will be useful for auditing and troubleshooting network bottlenecks later on.
