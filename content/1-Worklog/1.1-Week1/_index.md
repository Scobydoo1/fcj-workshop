# ☁️ AWS Training Worklog: Week 1 - Core Foundations

**Status:** 🟢 Completed  
**Timeframe:** 05/01/2025 - 11/01/2025  
**Objective:** Establish a secure, monitored baseline AWS environment and understand identity management to prepare for upcoming cloud deployments.

This document serves as my detailed technical worklog for Week 1 of my AWS training. It tracks my daily progress, configurations applied, and challenges overcome as I build a foundational understanding of AWS infrastructure.

---

## 📅 Daily Task Log

### Module 1.1: Account Setup & Initialization
* **Date Completed:** 05/01/2025
* **Time Spent:** 1.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Registered a new AWS Free Tier account.
- [x] Secured the Root user (Enabled MFA, generated strong password).
- [x] Explored the AWS Management Console UI and regions.

**Notes & Observations:**
> Set the default region to `ap-southeast-1` (Singapore) for optimal latency. This environment will eventually serve as the foundation for hosting our React frontends and Java Spring Boot microservices, so getting the baseline security right is critical.

---

### Module 1.2: Cost Management (AWS Budgets)
* **Date Completed:** 06/01/2025
* **Time Spent:** 2.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Accessed the AWS Billing Dashboard.
- [x] Created a Zero-Spend budget to track Free Tier limits.
- [x] Configured an alerting system to notify my email when forecasted spend exceeds $0.01.

**Troubleshooting / Learnings:**
> There was a slight delay (about 24 hours) for billing data to propagate in the dashboard after account creation. Configured the alerts to ensure no surprise charges occur during testing.

**Artifacts:**
- 🖼️ `[budget-alert-config-20250106.png]`

---

### Module 1.3: Utilizing AWS Support
* **Date Completed:** 08/01/2025
* **Time Spent:** 0.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Reviewed the different AWS Support Plans (Basic, Developer, Business, Enterprise).
- [x] Navigated the Support Center console.
- [x] Reviewed documentation on how to properly format technical inquiries for fast resolution.

**Key Takeaway:**
> Currently on the Basic support plan, which is sufficient for account and billing inquiries. For technical troubleshooting on architectural issues later on, we would need to upgrade to at least Developer or Business tier.

---

### Module 1.4: Security & Identity (AWS IAM)
* **Date Completed:** 10/01/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

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

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully locked down the root account, established billing guardrails, and set up a secure IAM admin user for everyday development. 
* **Concepts to review later:** Deep dive into IAM Policy JSON structures (Condition blocks, specific resource ARNs) to better restrict access for specific application roles.
