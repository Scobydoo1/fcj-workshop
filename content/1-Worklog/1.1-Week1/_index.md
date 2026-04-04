---
title: "Week 1 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

### Week 1 Objectives:

* Connect and get acquainted with members of First Cloud Journey.
* Understand the fundamentals of AWS Cloud: infrastructure, service categories, and the Shared Responsibility Model.
* Set up a secure AWS account with billing controls and IAM best practices.
* Learn and practice AWS IAM: Users, Groups, Roles, and Policies.
* Install and configure AWS CLI for programmatic access.
* Launch, connect to, and manage a first Amazon EC2 instance.

---

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Get acquainted with FCJ members and mentors <br> - Read internship rules, regulations, and expectations <br> - **AWS Cloud Overview:** <br>&emsp; + What is Cloud Computing? (IaaS, PaaS, SaaS) <br>&emsp; + On-premises vs. Cloud vs. Hybrid <br>&emsp; + AWS Global Infrastructure: Regions, Availability Zones, Edge Locations <br>&emsp; + AWS Shared Responsibility Model <br>&emsp; + AWS Well-Architected Framework (6 pillars overview) | 11/08/2025 | 11/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 3 | - **Getting Started with AWS — Create Your First Account:** <br>&emsp; + Sign up at aws.amazon.com (Free Tier) <br>&emsp; + Verify email and add payment method <br>&emsp; + Enable **MFA** on root account (Google Authenticator / Authy) <br>&emsp; + **Never** use root for daily tasks <br> - **AWS Budgets:** <br>&emsp; + Create Cost Budget at $10/month <br>&emsp; + Set alert at 80% actual and 100% forecasted <br>&emsp; + Add email notification <br> - **AWS Support Plans:** Basic / Developer / Business / Enterprise <br> - **AWS Pricing Calculator:** estimate EC2 t2.micro cost in ap-southeast-1 | 12/08/2025 | 12/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 4 | - **AWS IAM:** Users, Groups, Roles, Policies <br>&emsp; + Inline vs. Managed vs. Customer Managed Policy <br>&emsp; + Principle of Least Privilege <br>&emsp; + Policy JSON: `Effect`, `Action`, `Resource`, `Condition` <br> - **Practice:** <br>&emsp; 1. Create IAM Group `AdminGroup` + attach `AdministratorAccess` <br>&emsp; 2. Create IAM User `admin-user` → add to group <br>&emsp; 3. Enable MFA for IAM user <br>&emsp; 4. Set Password Policy (12+ chars, complexity) <br>&emsp; 5. Download `.csv` credentials <br>&emsp; 6. Sign in as `admin-user` and verify | 13/08/2025 | 13/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 5 | - **IAM Roles for EC2:** Trust Policy + Permission Policy + Instance Profile <br> - **Practice:** Create Role `EC2-S3-ReadOnly-Role` (trusted entity: EC2, policy: `AmazonS3ReadOnlyAccess`) <br> - **AWS CLI v2:** install + `aws configure` (Access Key, Secret Key, region `ap-southeast-1`, output `json`) <br> - **CLI commands:** `aws sts get-caller-identity` · `aws iam list-users` · `aws iam list-groups` · `aws ec2 describe-regions --output table` · `aws ec2 describe-availability-zones --region ap-southeast-1` | 14/08/2025 | 14/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 6 | - **EC2 Concepts:** instance families, AMI, Key Pairs, Security Groups, Elastic IP, EBS types, pricing models <br> - **Practice — Launch EC2:** <br>&emsp; 1. Name: `MyFirstEC2` · AMI: Amazon Linux 2023 · Type: t2.micro <br>&emsp; 2. Create key pair `my-key-pair` → download `.pem` <br>&emsp; 3. Security Group: allow SSH port 22 from My IP only <br>&emsp; 4. Attach IAM Instance Profile: `EC2-S3-ReadOnly-Role` <br>&emsp; 5. Launch → wait for running state <br> - **SSH:** `chmod 400 my-key-pair.pem` → `ssh -i "my-key-pair.pem" ec2-user@<Public-IP>` <br> - **EBS:** Create 5 GiB gp3 volume → Attach as `/dev/xvdb` → `mkfs.ext4` → `mount /dev/xvdb /data` → `df -h` <br> - **Elastic IP:** Allocate → Associate to instance → verify IP is persistent | 15/08/2025 | 15/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |

---

### Week 1 Achievements:

* **AWS Cloud Fundamentals:** IaaS/PaaS/SaaS, Global Infrastructure (Regions/AZs/Edge), Shared Responsibility Model, Well-Architected Framework 6 pillars

* **AWS Account & Cost Control:**
  * Free Tier account created with MFA on root
  * AWS Budgets alert at $10/month (80% + 100% thresholds)
  * Understood all 4 AWS Support plan tiers

* **AWS IAM:**
  * Created `AdminGroup` with `AdministratorAccess` policy
  * Created `admin-user` with MFA — root account no longer used
  * Applied Least Privilege, password policy, IAM best practices
  * Understood Policy JSON structure (`Effect`, `Action`, `Resource`, `Condition`)

* **IAM Roles for EC2:**
  * Created `EC2-S3-ReadOnly-Role` with EC2 trust policy
  * Attached as Instance Profile — no static credentials embedded in instance

* **AWS CLI:**
  * Installed CLI v2, configured with `aws configure`
  * Ran: `get-caller-identity`, `list-users`, `describe-regions`, `describe-availability-zones`

* **Amazon EC2:**
  * Launched Amazon Linux 2023 t2.micro (Free Tier)
  * Connected via SSH with `.pem` key pair
  * Created, attached, formatted (`ext4`), and mounted EBS volume → `/data`
  * Allocated and associated Elastic IP (persistent public IP)
  * Verified all resources via Console and CLI
* ...
