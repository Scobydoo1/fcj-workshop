---
title: "Week 3 Worklog"
date: 2026-01-19
weight: 3
chapter: false
pre: "<b>1.3. </b>"
---

# ☁️ AWS Training Worklog: Week 3 - Storage, Databases & Auto Scaling

**Status:** 🟢 Completed  
**Timeframe:** 19/01/2025 - 25/01/2025  
**Objective:** Deploy scalable database solutions, configure secure object storage for frontend assets, and implement dynamic compute scaling.

This document tracks my Week 3 progress during my OJT at AWS. Building on the network topology established last week, this week's focus is on adding stateful storage, persistent data management, and high availability.

---

## 📅 Daily Task Log

### Module 3.1: Object Storage (Amazon S3)
* **Date Completed:** 20/01/2025
* **Time Spent:** 2.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Created a new Amazon S3 bucket with a globally unique name.
- [x] Disabled "Block Public Access" and attached a custom JSON Bucket Policy to allow public read access to specific objects.
- [x] Enabled Static Website Hosting on the bucket.
- [x] Uploaded a sample `index.html` and `error.html` to test the endpoint.

**Notes & Observations:**
> S3 static hosting is incredibly cost-effective. This setup is perfectly suited for hosting the compiled static assets of our React frontends without needing to provision dedicated web servers.

**Artifacts:**
- 📄 `[s3-public-read-policy.json]`

---

### Module 3.2: Relational Databases (Amazon RDS)
* **Date Completed:** 22/01/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Configured a DB Subnet Group targeting the Private Subnets created in Week 2.
- [x] Provisioned a Free Tier MySQL RDS instance (db.t3.micro).
- [x] Configured the RDS Security Group to strictly allow inbound traffic on Port 3306 only from the EC2 application server's Security Group.
- [x] Connected to the database from the bastion EC2 instance using the MySQL CLI client.

**Troubleshooting / Learnings:**
> Placing the RDS instance in the private subnet ensures it has no public IP, protecting it from direct internet exposure. This database topology is exactly what I need to securely connect the Java Spring Boot backends I will be deploying later.

**Artifacts:**
- 🖼️ `[rds-connectivity-success-20250122.png]`

---

### Module 3.3: High Availability (Amazon EC2 Auto Scaling)
* **Date Completed:** 24/01/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Created an EC2 Launch Template with the pre-configured AMI and Security Groups from Week 2.
- [x] Defined an Auto Scaling Group (ASG) spanning multiple public subnets.
- [x] Set Minimum, Desired, and Maximum capacity limits (e.g., Min: 1, Max: 3).
- [x] Configured a Target Tracking Scaling Policy to add instances if average CPU utilization exceeds 70%.
- [x] Stress-tested the primary instance to trigger a scale-out event.

**Notes & Observations:**
> Watching the ASG automatically spin up a new instance during the stress test was a great demonstration of cloud elasticity.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully isolated the database layer in a private network while maintaining secure access, and achieved automated high availability for compute resources.
* **Concepts to review later:** Need to practice creating cross-account S3 replication policies, and look into RDS Read Replicas for database scaling.
