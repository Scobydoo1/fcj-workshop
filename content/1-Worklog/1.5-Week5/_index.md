---
title: "Week 5 Worklog"
date: 2026-02-02
weight: 5
chapter: false
pre: "<b>1.5. </b>"
---

# ☁️ AWS Training Worklog: Week 5 - Capstone: Highly Available Web Application

**Status:** 🟢 Completed  
**Timeframe:** 02/02/2025 - 08/02/2025  
**Objective:** Integrate core AWS services to architect and deploy a resilient, highly available 3-tier web application.

This document tracks my Week 5 progress. This week serves as the culmination of the foundational training, executing the "Highly Available Web Application Workshop."

---

## 📅 Daily Task Log

### Module 5.1: Architecture Design & Network Preparation
* **Date Completed:** 03/02/2025
* **Time Spent:** 2.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Reviewed the 3-tier architecture blueprint provided in the workshop.
- [x] Audited the VPC to ensure public subnets are ready for Load Balancers and private subnets are isolated for Application Servers and Databases.
- [x] Configured a centralized Security Group matrix (ALB -> EC2 -> RDS) to enforce strict traffic flow.

---

### Module 5.2: Deploying the Data Tier (Multi-AZ RDS)
* **Date Completed:** 05/02/2025
* **Time Spent:** 3.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Upgraded the single-node RDS instance from Week 3 into a Multi-AZ deployment.
- [x] Verified the standby replica in the secondary Availability Zone.
- [x] Executed a manual reboot with failover to test database resilience and monitor downtime.

---

### Module 5.3: Compute Tier & Application Load Balancing
* **Date Completed:** 06/02/2025
* **Time Spent:** 4.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Provisioned an Application Load Balancer (ALB) across two public subnets.
- [x] Updated the EC2 Auto Scaling Group to register instances automatically with the ALB Target Group.
- [x] Deployed a sample backend API on the EC2 instances using a User Data bootstrap script.
- [x] Configured Health Checks on the ALB to ensure traffic is only routed to healthy instances.

**Artifacts:**
- 🖼️ `[alb-target-group-healthy.png]`
- 📄 `[ec2-bootstrap-userdata.sh]`

---

### Module 5.4: Frontend Integration & End-to-End Testing
* **Date Completed:** 08/02/2025
* **Time Spent:** 3.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Hosted the frontend application assets on the S3 bucket.
- [x] Updated the frontend API configuration to point to the newly created ALB DNS name.
- [x] Used Route 53 to map a custom domain to the ALB.
- [x] Performed an end-to-end stress test to observe the ASG scaling out and the ALB distributing traffic evenly.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully deployed a fully functional, highly available 3-tier architecture capable of self-healing and automatic scaling.
* **Concepts to review later:** Integrating AWS Certificate Manager (ACM) to enable HTTPS on the Application Load Balancer.
