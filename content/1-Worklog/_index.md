---
title: "Worklog"
date: 2026-01-05
weight: 1
chapter: true
pre: "<b>1. </b>"
---

# 🚀 10-Week AWS & SmartHire Engineering Journey: Complete Summary

**Status:** 🟢 Completed  
**Timeframe:** January 2026 - March 2026  
**Project:** SmartHire AI & AWS Cloud Infrastructure  

This document provides a high-level summary of my 10-week On-the-Job Training (OJT) journey. The training was divided into two major phases: establishing foundational cloud infrastructure and developing a cloud-native, AI-powered recruitment platform.

---

## 🏗️ Phase 1: AWS Core Foundations (Weeks 1–5)
The first half of the training focused on establishing a secure, resilient, and scalable cloud infrastructure capable of hosting enterprise applications.

* **Week 1 (Security & Governance):** Locked down the root account, established zero-spend billing alarms, and implemented strict Identity and Access Management (IAM) policies with MFA for daily administrative access.
* **Week 2 (Networking & Compute):** Architected a custom Virtual Private Cloud (VPC) with public/private subnets and deployed the first Ubuntu EC2 instances securely accessed via SSH and assigned IAM roles.
* **Week 3 (Storage, Databases & Scaling):** Set up Amazon S3 for static hosting, isolated a MySQL database in a private subnet using RDS, and configured an Auto Scaling Group (ASG) to handle traffic spikes automatically.
* **Week 4 (Observability & Routing):** Gained system visibility using custom CloudWatch dashboards and alarms, and configured Route 53 for hybrid DNS traffic routing.
* **Week 5 (Capstone Architecture):** Brought all foundational pieces together to deploy a highly available, fault-tolerant 3-tier web application utilizing Application Load Balancers (ALB) and Multi-AZ database failover.

---

## 💻 Phase 2: SmartHire AI Development (Weeks 6–10)
The second half shifted entirely to application development, focusing on building the SmartHire AI portal using React/Vite and integrating it with AWS cloud-native services.

* **Week 6 (Project Kickoff & Auth):** Scaffolded the React repository and established a secure, role-based authentication flow (Candidate vs. Recruiter) using Amazon Cognito, served securely via CloudFront.
* **Week 7 (Candidate Portal & S3 Uploads):** Built the candidate dashboard using modern UI components (shadcn) and engineered a highly efficient, direct-to-S3 CV upload mechanism using Pre-signed URLs to bypass backend bottlenecks.
* **Week 8 (Recruiter Portal & Real-Time Data):** Developed the recruiter job management interface and integrated AWS AppSync (GraphQL) to stream real-time candidate AI evaluation scores directly to the front-end via WebSockets.
* **Week 9 (Interview Workspace):** Focused on complex state management for the live interview room, integrating WebRTC, microphone volume tracking, and emotion analysis hooks.
* **Week 10 (CI/CD & Polishing):** Finalized the user experience with global Theme Management (Dark Mode) and automated the deployment lifecycle by building a GitHub Actions CI/CD pipeline that securely syncs code to S3 and invalidates the CloudFront cache via OIDC.

---
*End of 10-Week OJT Worklog*
