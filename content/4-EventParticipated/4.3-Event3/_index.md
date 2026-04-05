# 📅 Events Participated: Summary Reports

---

## Summary Report: “Cloud Mastery #2 - Infrastructure as Code with Terraform”

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
    * **Automation-first approach:** Infrastructure should be treated exactly like application code—versioned, reviewed, and tested.
* **Technical Architecture**
    * **Stateful tracking:** Understanding how Terraform tracks changes helps prevent infrastructure drift and unauthorized modifications.
* **Modernization Strategy**
    * Choose the right tool for the team: Terraform for multi-cloud, AWS CDK for developer-centric logic, or CloudFormation for native AWS setups.

### Applying to Work
* **Apply IaC to current projects:** Transition the SmartHire AI cloud environment from manual setup to Terraform templates.
* **Implement CI/CD integration:** Automate `terraform plan` and `apply` within GitHub Actions workflows.

### Event Experience
Attending the **“Cloud Mastery #2”** workshop was extremely valuable, giving me a comprehensive view of modernizing infrastructure provisioning. Key experiences included:
* **Learning from highly skilled speakers:** Thinh shared real-world perspectives on the pitfalls of manual "ClickOps" and how to overcome them.
* **Hands-on technical exposure:** Learned how to safely preview changes with `terraform plan` and manage state files securely.
* **Leveraging modern tools:** Explored Terraform alongside considerations for other tools like Pulumi and OpenTofu.
* **Lessons learned:** Manual cloud management is only good for learning; production environments absolutely require IaC for consistency and collaboration.

### Some event photos
*[Add your event photos here]*

**Overall, the event not only provided technical knowledge but also helped me reshape my thinking about infrastructure reliability, team collaboration, and automated deployments.**

---

## Summary Report: “Architecting for the Cloud with Kubernetes”

### Event Objectives
* Share best practices in container orchestration and microservices deployment.
* Introduce the architecture and core components of Kubernetes (K8s).
* Provide guidance on running production-grade clusters using Amazon EKS.
* Present essential tools like Helm and K9s to support the cluster management lifecycle.

### Speakers
* **Bao Huynh** – Junior Cloud Native Developer, Endava Vietnam / Founder of ITea Lab

### Key Highlights
* **Identifying the drawbacks of basic container setups**
    * Docker Compose works well locally but struggles with self-healing, scaling, and load balancing in production.
* **Transitioning to Kubernetes Orchestration**
    * **Core Architecture:** Control Plane vs. Worker Nodes. Understanding Pods, Deployments, and Services.
    * **Amazon EKS:** AWS manages the Kubernetes control plane, removing the heavy lifting of maintaining highly available cluster infrastructure manually.
* **Kubernetes Ecosystem Tools**
    * **Helm:** Acts as the package manager for K8s, allowing teams to use versioned, shareable templates (`values.yaml`) for different environments.
    * **K9s:** A terminal-based UI to interact with clusters, making it much faster to check logs and monitor pods compared to standard `kubectl` commands.

### Key Takeaways
* **Design Mindset**
    * **Resilience by design:** Systems should automatically restart failed containers and distribute traffic seamlessly.
* **Technical Architecture**
    * **Managed Kubernetes:** Using Amazon EKS is far more efficient than self-hosting a Kubernetes cluster from scratch.
* **Modernization Strategy**
    * Standardize deployments across Dev, Staging, and Prod using Helm charts.

### Applying to Work
* **Refactor microservices:** Ensure application components are properly containerized and stateless to fit orchestration requirements.
* **Adopt EKS tools:** Pilot Helm charts for deploying our backend services.

### Event Experience
Attending the **“Architecting for the Cloud with Kubernetes”** workshop was extremely valuable, giving me a comprehensive view of scaling applications. Key experiences included:
* **Learning from highly skilled speakers:** Bao Huynh provided a clear path from Docker basics to enterprise Kubernetes architecture.
* **Hands-on technical exposure:** Learned how K8s manifests work and how to navigate clusters rapidly using K9s.
* **Lessons learned:** Managing raw infrastructure is complex; leveraging managed services like EKS and package managers like Helm drastically reduces operational overhead.

### Some event photos
*[Add your event photos here]*

**Overall, the event not only provided technical knowledge but also helped me reshape my thinking about high availability, microservices orchestration, and modern cloud-native operations.**

---

## Summary Report: “Elixir as a Unified Solution for DevOps Infrastructure”

### Event Objectives
* Share best practices in building highly concurrent and fault-tolerant backend systems.
* Introduce the functional programming paradigm and the BEAM virtual machine.
* Provide guidance on error handling using OTP and the "Let It Crash" philosophy.
* Present real-world cost optimization strategies replacing traditional serverless setups.

### Speakers
* **Nguyen Ta Minh Triet** – R&D Member, ITea Lab / SAP Developer Intern

### Key Highlights
* **Identifying the drawbacks of traditional concurrency models**
    * Standard OS-level threads are heavy and expensive.
    * Defensive programming with excessive `try/catch` statements pollutes codebases.
* **Transitioning to Elixir and the BEAM VM**
    * **Lightweight Processes:** BEAM processes use minimal memory, allowing millions of concurrent processes on a single machine.
    * **"Let It Crash" Philosophy:** Instead of rescuing every error, supervised processes are simply allowed to die and get immediately relaunched to a clean state by a Supervisor.
* **Real-World Cost Optimization**
    * **Case Study:** Rewriting an AWS API Gateway + Lambda (Node.js) event ingestion pipeline in Elixir reduced costs drastically. (e.g., A high-traffic workload went from $30,000+/month in serverless fees to under $400/month using an Elixir backend).
* **Hot Code Upgrades:** Deploying new system versions without any downtime.

### Key Takeaways
* **Design Mindset**
    * **Fault-tolerance first:** Systems should be designed to recover instantly from unexpected errors rather than trying to prevent every possible failure.
* **Technical Architecture**
    * **Actor Model:** Practical method for isolating state and handling massive concurrency without traditional locking mechanisms.
* **Modernization Strategy**
    * While serverless (Lambda) is great for many use cases, highly concurrent, constant-stream applications might achieve better ROI using efficient languages like Elixir on persistent compute.

### Applying to Work
* **Evaluate compute choices:** Carefully assess whether a workload is best suited for Serverless (event-driven, sporadic) or persistent compute (high constant concurrency) to optimize ROI.
* **Apply supervision patterns:** Implement similar self-healing and automated restart concepts in current microservices architectures.

### Event Experience
Attending the **“Elixir in DevOps”** workshop was extremely valuable, giving me a comprehensive view of functional programming and system resilience. Key experiences included:
* **Learning from highly skilled speakers:** Gained insights into alternative architectures that challenge the standard serverless default.
* **Hands-on technical exposure:** Understood how the BEAM VM handles lightweight processes compared to Java or Node.js.
* **Leveraging modern tools:** Explored the concept of Hot Code Upgrades and Supervisor trees.
* **Lessons learned:** Technology choice directly impacts business ROI. Matching the right programming paradigm (e.g., Elixir for high concurrency) to the right problem can save organizations tens of thousands of dollars.

### Some event photos
*[Add your event photos here]*

**Overall, the event not only provided technical knowledge but also helped me reshape my thinking about system reliability, concurrency models, and the financial impact of architecture choices.**