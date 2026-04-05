---
title: "Event 3"
date: 2026-04-04
weight: 3
chapter: false
pre: " <b> 4.3 </b> "
---

# 📅 Events Participated: Summary Reports

---

## Summary Report: "Cloud Mastery #2 – Infrastructure as Code with Terraform"

### Event Objectives
* Share best practices in transitioning from manual cloud provisioning to automated deployments.
* Introduce the core concepts of Infrastructure as Code (IaC).
* Provide guidance on selecting IaC tools (Terraform vs. CloudFormation vs. AWS CDK).
* Present practical demonstrations of Terraform state management and basic commands on AWS.

### Speakers
* **Thinh Nguyễn** – FCAJ Cloud Engineer Trainee

### Key Highlights
* **Identifying the drawbacks of the "ClickOps" way**
    * Manual configuration via the console is slow and prone to human error.
    * Inconsistency across environments (Dev, Staging, Prod).
    * Collaboration problems and lack of version control for infrastructure changes.
* **Transitioning to Infrastructure as Code (IaC)**
    * Managing cloud resources through machine-readable definition files.
    * **Terraform ecosystem:** Understanding the declarative approach to define *what* the infrastructure should look like rather than *how* to build it.
* **Terraform Core Mechanics**
    * Deep dive into commands: `init`, `validate`, `plan`, `apply`, and `destroy`.
    * **State Management:** How `terraform.tfstate` acts as the source of truth mapping configurations to real-world AWS resources.

### Key Takeaways
* **Design Mindset**
    * **Automation-first approach:** Infrastructure should be treated exactly like application code — versioned, reviewed, and tested.
* **Technical Architecture**
    * **Stateful tracking:** Understanding how Terraform tracks changes helps prevent infrastructure drift and unauthorized modifications.
* **Modernization Strategy**
    * **Choose the right tool for the team:** Terraform for multi-cloud, AWS CDK for developer-centric logic, or CloudFormation for native AWS setups.

### Applying to Work
* **Migrate manual configurations to Terraform:** Start versioning existing infrastructure into `.tf` files.
* **Implement state locking:** Use S3 + DynamoDB backend to safely manage `terraform.tfstate` in team environments.
* **Introduce IaC into the CI/CD pipeline:** Automate `terraform plan` and `apply` as part of deployment workflows.

### Event Experience
Attending the **"Cloud Mastery #2 – Infrastructure as Code with Terraform"** event at FPT University was an extremely rewarding experience. Key highlights included:
* **Learning from a fellow trainee:** Thinh's practical, hands-on perspective made the material highly relatable and easy to apply.
* **Deep technical exposure:** The live `terraform plan` and `apply` demonstrations clarified the full IaC workflow from code to cloud resource.
* **Networking and discussions:** Met other cloud trainees and had productive conversations about best practices for managing infrastructure at scale.
* **Lessons learned:** IaC is not just about automation — it is about bringing software engineering discipline (version control, code reviews, testing) to infrastructure management.

### Some event photos
*[Add your event photos here]*

**Overall, the event reinforced that treating infrastructure as code is a fundamental shift in thinking — one that dramatically improves consistency, collaboration, and confidence in cloud deployments.**
