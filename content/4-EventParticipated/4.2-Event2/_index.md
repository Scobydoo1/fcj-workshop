---
title: "Event 2"
date: 2026-03-14
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

# 📅 Events Participated: Summary Reports

---

## Summary Report: "AIoT Project: Locker Management"

### Event Objectives
* Share best practices in automating manual physical processes with cloud technologies.
* Introduce edge-to-cloud architectures using Arduino and Raspberry Pi.
* Provide guidance on securely connecting IoT devices to AWS.
* Present AI tools (AWS Rekognition) to support physical identity verification.

### Speakers
* **Aiden Dinh** – Operation Engineer, Katalon

### Key Highlights
* **Identifying the drawbacks of manual management**
    * Manual tracking processes are highly redundant.
    * Inefficient operations → Managers might not be available every time a member wants to borrow items.
* **Transitioning to automated AIoT architecture**
    * **Hardware integration:** Utilizing Raspberry Pi as the Main Controller/MQTT Broker, and Arduino as the Edge Device collecting data from Reed Switches, RFID Card Readers, and Cameras.
    * **AWS IoT Core:** Secures connection and data transfer. Routes sensor events (RFID scans, door states) to Lambda, DynamoDB, and S3 without relying solely on a local MQTT server.
* **Facial Authentication Integration**
    * **AWS Rekognition:** Performs facial recognition to identify which club member is accessing the locker. Compares images against a pre-trained face collection and returns similarity confidence scores to link identity with RFID transactions.

### Key Takeaways
* **Design Mindset**
    * **Automation-first approach:** Always look for ways to eliminate manual redundancy in physical workflows.
* **Technical Architecture**
    * **Edge-to-Cloud:** Practical method for using Raspberry Pi to bridge local sensors with scalable AWS infrastructure.
    * Use **AWS IoT Core** instead of standalone local MQTT servers for secure, scalable event routing.
* **Modernization Strategy**
    * **Integrating AI with hardware:** Combining hardware sensors (RFID) with AI (Rekognition) creates a highly secure, multi-factor authentication system.

### Applying to Work
* **Apply IoT Architecture to current projects:** Utilize AWS IoT Core for secure data ingestion from edge devices.
* **Implement AI validation:** Pilot AWS Rekognition for workflows requiring identity verification.

### Event Experience
Attending the **"AIoT Project: Locker Management"** workshop was extremely valuable, giving me a comprehensive view of integrating edge hardware with AWS cloud-native AI. Key experiences included:
* **Learning from highly skilled speakers:** Aiden shared best practices in building automated IoT systems.
* **Hands-on technical exposure:** Learned how to route sensor events from Raspberry Pi to AWS Lambda and DynamoDB. Understood the trade-offs of local MQTT vs. AWS IoT Core.
* **Leveraging modern tools:** Explored AWS Rekognition for facial authentication and linking physical RFID scans with digital identities.
* **Networking and discussions:** The workshop offered opportunities to exchange ideas about hardware-cloud bridging.
* **Lessons learned:** Applying AIoT architectures improves system security and reduces manual operational overhead.

### Some event photos
*[Add your event photos here]*

**Overall, the event not only provided technical knowledge but also helped me reshape my thinking about physical-digital system integration and edge computing on AWS.**

---

## Summary Report: "Building AI Agent with Strands"

### Event Objectives
* Share best practices in modern Generative AI application design.
* Introduce the transition from standalone LLMs to autonomous AI Agents.
* Provide guidance on selecting and integrating tools (APIs, databases).
* Present the Strands framework to support the agentic development lifecycle.

### Speakers
* **Banh Cam Vinh**

### Key Highlights
* **Identifying the drawbacks of standalone LLMs**
    * Inability to fetch real-time data → Hallucinations and outdated responses.
    * Lack of execution capabilities → Cannot take actions on behalf of the user.
* **Transitioning to Agentic Architecture**
    * **Multi-step reasoning:** Agents can plan and execute complex workflows automatically.
    * **Tool integration:** Allowing the LLM to access APIs, databases, and external services.
    * **Agentic Loop (Tool Calling):** The process where the AI decides which tool to use, waits for the result, and formulates the next step.
* **System Prompts & Knowledge Bases**
    * Defining strict autonomous behaviors and integrating domain-specific knowledge to adapt responses based on the current context.

### Key Takeaways
* **Design Mindset**
    * **Action-oriented approach:** Move beyond static chatbots to dynamic, decision-making agents.
* **Technical Architecture**
    * **Tool Calling:** Practical method for modeling workflows where AI interacts with external systems.
* **Modernization Strategy**
    * Adopt frameworks like Strands to standardize how tools and system prompts are integrated into LLM applications.

### Applying to Work
* **Apply Agentic workflows to current projects:** Upgrade standard chat interfaces to autonomous agents that can trigger backend functions.
* **Implement tool calling:** Connect current project databases and APIs to the LLM.

### Event Experience
Attending the **"Building AI Agent with Strands"** workshop was extremely valuable, giving me a comprehensive view of modernizing AI applications. Key experiences included:
* **Learning from highly skilled speakers:** Gained deep insights into multi-step reasoning and autonomous behavior.
* **Hands-on technical exposure:** Learned how to build the Agentic Loop and define tools within the Strands framework.
* **Lessons learned:** Relying solely on LLMs limits application capability; integrating tools allows for real-time data access and dynamic responses.

### Some event photos
*[Add your event photos here]*

**Overall, the event not only provided technical knowledge but also helped me reshape my thinking about AI application design and autonomous workflows.**

---

## Summary Report: "Automated Prompt Engineering: Enhancing LLM Output Quality"

### Event Objectives
* Share best practices in prompt engineering and the "art of communicating with AI."
* Introduce structured prompt components to eliminate ambiguous instructions.
* Provide guidance on building an automated, serverless prompt optimization architecture.
* Present AWS tools (Bedrock, CloudWatch) to support GenAIOps and observability.

### Speakers
* **Nguyen Tuan Thinh** – DevOps Engineer, First Cloud AI Journey

### Key Highlights
* **Identifying the drawbacks of poor communication with AI**
    * Generic prompts → Generic, unusable outputs.
    * Ambiguous instructions → Inconsistent results across different runs.
    * Wasted tokens → Increased API costs and reduced productivity.
* **Transitioning to Structured Prompting**
    * **Key Components:** Role, Instruction, Context, Input Data, Output Format, Examples, Constraints/Guidelines.
* **Serverless GenAIOps Architecture**
    * **Amazon Bedrock:** Serves as the core LLM engine without requiring manual model training.
    * **Amazon DynamoDB:** NoSQL database for storing user data, prompts, and optimization history with millisecond response times.
    * **Amazon CloudWatch:** Collects logs and tracks application performance metrics (API latency, error rates) for real-time system health monitoring.

### Key Takeaways
* **Design Mindset**
    * **Structure-first approach:** Always formulate prompts systematically rather than treating them as casual conversation.
* **Technical Architecture**
    * **GenAIOps:** Practical method for modeling and monitoring generative AI workflows in production.
    * Use **CloudWatch metrics** to observe API latency and token usage.
* **Modernization Strategy**
    * Implement **Amazon Bedrock** for scalable, managed foundation models instead of hosting heavy models on EC2.

### Applying to Work
* **Apply structured prompting to current projects:** Refactor all application prompts to include the 7 core components (Role, Context, Constraints, etc.).
* **Adopt GenAIOps:** Pilot Amazon CloudWatch to monitor Bedrock API latency and error rates in our environments.

### Event Experience
Attending the **"Automated Prompt Engineering"** workshop was extremely valuable, giving me a comprehensive view of optimizing LLMs using advanced methods and tools. Key experiences included:
* **Learning from highly skilled speakers:** The DevOps perspective on GenAI highlighted the importance of cost-efficiency and token management.
* **Hands-on technical exposure:** Learned how to use DynamoDB for storing prompt histories and CloudWatch for observing AI system health.
* **Lessons learned:** Well-engineered prompts reduce token waste while improving output resilience. Monitoring AI applications is just as critical as monitoring traditional microservices.

### Some event photos
*[Add your event photos here]*

**Overall, the event not only provided technical knowledge but also helped me reshape my thinking about prompt engineering, system observability, and cost-optimization in the GenAI era.**
