---
title: "Week 4 Worklog"
date: 2026-01-26
weight: 4
chapter: false
pre: "<b>1.4. </b>"
---

# ☁️ AWS Training Worklog: Week 4 - Monitoring, DNS & Dev Tools

**Status:** 🟢 Completed  
**Timeframe:** 26/01/2025 - 01/02/2025  
**Objective:** Implement system observability, configure hybrid DNS routing, and explore integrated cloud developer environments.

This document tracks my Week 4 progress during my AWS OJT. With storage, compute, and databases in place, this week focuses on gaining visibility into those resources, routing traffic securely, and streamlining the development workflow.

---

## 📅 Daily Task Log

### Module 4.1: Observability & Monitoring (Amazon CloudWatch)
* **Date Completed:** 27/01/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Configured the CloudWatch Agent on the existing EC2 instances to track memory and disk utilization.
- [x] Created a custom CloudWatch Dashboard centralizing EC2 CPU metrics, RDS connections, and ASG network traffic.
- [x] Set up CloudWatch Alarms to trigger an SNS email notification if database CPU utilization exceeds 80% for 5 minutes.
- [x] Explored CloudWatch Logs and log groups.

**Artifacts:**
- 🖼️ `[cloudwatch-custom-dashboard.png]`
- 📄 `[cloudwatch-agent-config.json]`

---

### Module 4.2: DNS & Traffic Routing (Amazon Route 53)
* **Date Completed:** 29/01/2025
* **Time Spent:** 3.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Created a Route 53 Hosted Zone.
- [x] Configured 'A' Records to route traffic to the EC2 Auto Scaling Group.
- [x] Configured Alias records mapping a subdomain directly to the S3 bucket configured for static website hosting in Week 3.
- [x] Set up an integrated hybrid DNS system between a simulated Local environment and the Amazon VPC.

---

### Module 4.3: Cloud IDE & Simplified Compute (Cloud9 & Lightsail)
* **Date Completed:** 31/01/2025
* **Time Spent:** 2.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Provisioned an AWS Cloud9 environment backed by a `t2.micro` EC2 instance.
- [x] Cloned a sample repository into the Cloud9 IDE and tested browser-based code editing and terminal access.
- [x] Deployed a pre-configured LAMP stack on Amazon Lightsail.
- [x] Analyzed the cost differences between Lightsail's fixed pricing and EC2's on-demand pricing.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Achieved full system visibility with custom CloudWatch dashboards and successfully routed DNS traffic to both compute instances and static storage.
* **Concepts to review later:** Need to look into Route 53 Health Checks and failover routing policies.
