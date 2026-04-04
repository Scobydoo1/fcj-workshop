---
title: "Week 1 Worklog"
date: 2026-01-05
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

### ☁️ AWS Training Worklog: Week 1 - Core Foundations

**Status:** 🟢 Completed  
**Timeframe:** 05/01/2026 - 11/01/2026  
**Objective:** Establish a secure, monitored baseline AWS environment and understand identity management to prepare for upcoming cloud deployments.

This document serves as my detailed technical worklog for Week 1 of my AWS training. It tracks my daily progress, configurations applied, and challenges overcome as I build a foundational understanding of AWS infrastructure.

---

### Week 1 Objectives:

* Establish a secure AWS account baseline with Root user protection and MFA.
* Set up billing guardrails and cost management alerts.
* Understand IAM fundamentals and create an Admin user for daily operations.

### Tasks carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | - Registered a new AWS Free Tier account <br> - Secured Root user (MFA, strong password) <br> - Explored AWS Management Console UI and regions | 05/01/2026 | 05/01/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 2 | - Accessed the AWS Billing Dashboard <br> - Created a Zero-Spend budget to track Free Tier limits <br> - Configured alerting to notify when forecasted spend exceeds $0.01 | 06/01/2026 | 06/01/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Reviewed AWS Support Plans (Basic, Developer, Business, Enterprise) <br> - Navigated the Support Center console <br> - Reviewed documentation on formatting technical inquiries | 08/01/2026 | 08/01/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Created IAM Admin User for daily tasks (avoiding Root account usage) <br> - Enabled MFA for IAM user via authenticator app <br> - Created IAM Group (`DevOps-Admins`) with `AdministratorAccess` policy <br> - Generated and stored Access Keys for AWS CLI usage | 10/01/2026 | 10/01/2026 | <https://cloudjourney.awsstudygroup.com/> |

---

### Module 1.1: Account Setup & Initialization
* **Date Completed:** 05/01/2026
* **Time Spent:** 1.5 hours
* **Status:** [x] Done

**Work Performed:**
- [x] Registered a new AWS Free Tier account.
- [x] Secured the Root user (Enabled MFA, generated strong password).
- [x] Explored the AWS Management Console UI and regions.

**Notes & Observations:**
> Set the default region to `ap-southeast-1` (Singapore) for optimal latency. This environment will eventually serve as the foundation for hosting our React frontends and Java Spring Boot microservices, so getting the baseline security right is critical.

---

### Module 1.2: Cost Management (AWS Budgets)
* **Date Completed:** 06/01/2026
* **Time Spent:** 2.0 hours
* **Status:** [x] Done

**Work Performed:**
- [x] Accessed the AWS Billing Dashboard.
- [x] Created a Zero-Spend budget to track Free Tier limits.
- [x] Configured an alerting system to notify my email when forecasted spend exceeds $0.01.

**Troubleshooting / Learnings:**
> There was a slight delay (about 24 hours) for billing data to propagate in the dashboard after account creation. Configured the alerts to ensure no surprise charges occur during testing.

**Artifacts:**
- 🖼️ `[budget-alert-config-20260106.png]`

---

### Module 1.3: Utilizing AWS Support
* **Date Completed:** 08/01/2026
* **Time Spent:** 0.5 hours
* **Status:** [x] Done

**Work Performed:**
- [x] Reviewed the different AWS Support Plans (Basic, Developer, Business, Enterprise).
- [x] Navigated the Support Center console.
- [x] Reviewed documentation on how to properly format technical inquiries for fast resolution.

**Key Takeaway:**
> Currently on the Basic support plan, which is sufficient for account and billing inquiries. For technical troubleshooting on architectural issues later on, we would need to upgrade to at least Developer or Business tier.

---

### Module 1.4: Security & Identity (AWS IAM)
* **Date Completed:** 10/01/2026
* **Time Spent:** 3.5 hours
* **Status:** [x] Done

**Work Performed:**
- [x] Created an IAM Admin User for daily tasks (avoiding Root account usage).
- [x] Enabled MFA for the new IAM user via an authenticator app.
- [x] Created an IAM Group (`DevOps-Admins`) and attached the `AdministratorAccess` policy.
- [x] Generated and securely stored Access Keys for future AWS CLI usage.
- [x] Logged in via the IAM User sign-in URL.

**Challenges Faced & Resolutions:**
> Carefully reviewed IAM roles and policies to understand the principle of least privilege. This will be highly relevant soon when configuring IAM roles for services like the AWS Sentinel log anomaly detection system to securely access CloudWatch and S3 without hardcoded credentials.

**Artifacts:**
- 📄 `[admin-group-policy-trust.json]`
- 🖼️ `[iam-security-hub-green.png]`

---

### Week 1 Achievements:

* Successfully locked down the root account and established billing guardrails.
* Set up a secure IAM admin user for everyday development.
* Understood the principle of least privilege and how IAM groups/policies work.
* Reviewed all AWS Support Plan tiers and their appropriate use cases.

**Concepts to review later:** Deep dive into IAM Policy JSON structures (Condition blocks, specific resource ARNs) to better restrict access for specific application roles.
