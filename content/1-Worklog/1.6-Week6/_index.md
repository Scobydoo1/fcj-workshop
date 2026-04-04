---
title: "Week 6 Worklog"
date: 2026-02-09
weight: 6
chapter: false
pre: "<b>1.6. </b>"
---

# ☁️ AWS Training Worklog: Week 6 - SmartHire Project Kickoff & AWS Auth

**Status:** 🟢 Completed  
**Timeframe:** 09/02/2025 - 15/02/2025  
**Objective:** Initialize the SmartHire AI front-end architecture, configure static cloud hosting, and integrate Amazon Cognito for secure candidate and recruiter authentication.

This week marks the transition from foundational AWS learning to applied project development. I officially kicked off the front-end development for **SmartHire**, an AI-powered recruitment platform.

---

## 📅 Daily Task Log

### Module 6.1: Front-end Scaffolding & AWS Hosting Prep
* **Date Completed:** 10/02/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Initialized the `SmartHire-AI-dev` front-end repository using Vite, React, and TypeScript.
- [x] Configured Tailwind CSS and basic routing structures for Guest, Candidate, and Recruiter views.
- [x] Provisioned an Amazon S3 bucket designated for hosting the production build artifacts.
- [x] Set up an Amazon CloudFront distribution pointing to the S3 origin.

---

### Module 6.2: Identity Management (Amazon Cognito Setup)
* **Date Completed:** 12/02/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Created a new Amazon Cognito User Pool specifically for the SmartHire application.
- [x] Configured custom user attributes to distinguish between `Candidate` and `Recruiter` roles.
- [x] Set up password policies and enabled email verification for new sign-ups.
- [x] Created Cognito App Clients and documented the Client IDs for front-end environment variables.

---

### Module 6.3: React Authentication Components
* **Date Completed:** 14/02/2025
* **Time Spent:** 4.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `AuthLayout.tsx` to handle the UI shell for login and registration screens.
- [x] Created custom React hooks (`useAuthLogin.ts`, `useAuthRegister.ts`) to encapsulate the AWS Cognito SDK logic.
- [x] Built the `Login.tsx` and `Register.tsx` components with validation and error handling.
- [x] Implemented a `ProtectedRoute` wrapper to prevent unauthenticated access to the dashboard routes.

**Artifacts:**
- 📄 `[useAuthLogin.ts]`
- 🖼️ `[smarthire-login-ui-20250214.png]`

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully bridged the gap between a local React project and AWS by fully implementing a secure, cloud-backed authentication flow using Amazon Cognito.
* **Next Steps:** Moving into the Candidate and Recruiter dashboards, and preparing to connect the front-end to AWS AppSync for real-time data subscriptions.
