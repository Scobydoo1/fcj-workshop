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
* Learn the fundamentals of AWS cloud computing and core service categories.
* Complete the **Getting Started** and **IAM** sections from the FCJ Explore AWS Services path.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Get acquainted with FCJ members <br> - Read and take note of internship unit rules and regulations <br> - Overview of AWS Cloud: what is cloud computing, types of cloud (IaaS, PaaS, SaaS), AWS global infrastructure (Regions, AZs, Edge Locations) | 11/08/2025 | 11/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 3 | - **Getting Started with AWS** <br>&emsp; + Create your first AWS Account (Free Tier) <br>&emsp; + Enable MFA on the root account <br>&emsp; + Manage usage costs with **AWS Budgets** (set $10/month alert) <br>&emsp; + Understand AWS Support plans (Basic, Developer, Business, Enterprise) <br>&emsp; + Explore the AWS Management Console & AWS Pricing Calculator | 12/08/2025 | 12/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 4 | - **Identity and Access Management (IAM)** <br>&emsp; + IAM concepts: Users, Groups, Roles, Policies <br>&emsp; + Inline policy vs. Managed policy <br>&emsp; + Principle of Least Privilege <br>&emsp; + IAM Best Practices <br> - **Practice:** <br>&emsp; + Create an IAM admin user (avoid using root for daily tasks) <br>&emsp; + Create a user group and attach `AdministratorAccess` policy <br>&emsp; + Enable password policy for the account <br>&emsp; + Configure AWS CLI with Access Key & Secret Key | 13/08/2025 | 13/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 5 | - **IAM Roles for EC2** <br>&emsp; + Understand IAM Instance Profiles <br>&emsp; + Grant application permissions through IAM Roles (no hardcoded credentials) <br> - **AWS CLI basics** <br>&emsp; + `aws configure` — set up credentials and default region <br>&emsp; + `aws sts get-caller-identity` — verify identity <br>&emsp; + `aws iam list-users` — list IAM users <br>&emsp; + `aws ec2 describe-regions` — list all regions | 14/08/2025 | 14/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |
| 6 | - **Compute Essentials: Amazon EC2** <br>&emsp; + EC2 instance types & families (General Purpose, Compute Optimized, Memory Optimized, ...) <br>&emsp; + AMI (Amazon Machine Image) <br>&emsp; + Key Pairs, Security Groups, Elastic IP <br>&emsp; + EBS (Elastic Block Store) volumes <br>&emsp; + EC2 pricing models (On-Demand, Reserved, Spot, Savings Plans) <br> - **Practice:** <br>&emsp; + Launch an EC2 instance (Amazon Linux 2, t2.micro) <br>&emsp; + Connect via SSH using key pair <br>&emsp; + Attach and mount an additional EBS volume <br>&emsp; + Assign an Elastic IP to the instance | 15/08/2025 | 15/08/2025 | <https://cloudjourney.awsstudygroup.com/1-explore/> |


### Week 1 Achievements:

* Understood core AWS concepts:
  * Cloud computing models: IaaS, PaaS, SaaS
  * AWS global infrastructure: Regions, Availability Zones, Edge Locations
  * AWS Shared Responsibility Model

* Successfully created and secured an AWS Free Tier account:
  * MFA enabled on root account
  * AWS Budgets alert configured ($10/month threshold)
  * Billing & Cost Management dashboard explored

* Mastered AWS IAM fundamentals:
  * Created IAM admin user and user group
  * Attached `AdministratorAccess` managed policy to the group
  * Applied IAM best practices (no root usage, least privilege, password policy)
  * Understood the difference between IAM Users, Roles, Groups, and Policies

* Installed and configured AWS CLI:
  * `aws configure` with Access Key, Secret Key, Region (`ap-southeast-1`), Output (`json`)
  * Ran basic CLI commands to verify identity and list resources

* Launched a fully functional EC2 instance:
  * Amazon Linux 2, t2.micro (Free Tier eligible)
  * Connected via SSH using a `.pem` key pair
  * Attached and mounted an EBS volume
  * Assigned an Elastic IP address

* Understood EC2 pricing models and when to use each:
  * On-Demand, Reserved Instances, Spot Instances, Savings Plans
* ...
