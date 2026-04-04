---
title: "Week 8 Worklog"
date: 2026-02-23
weight: 8
chapter: false
pre: "<b>1.8. </b>"
---

# ☁️ AWS Training Worklog: Week 8 - Recruiter Dashboard & Real-Time AppSync

**Status:** 🟢 Completed  
**Timeframe:** 23/02/2025 - 01/03/2025  
**Objective:** Develop the Recruiter interface for job management and implement AWS AppSync GraphQL subscriptions to receive real-time candidate scoring updates.

With the Candidate flow functioning, this week I pivoted to the Recruiter side of SmartHire AI.

---

## 📅 Daily Task Log

### Module 8.1: Recruiter Layout & Navigation
* **Date Completed:** 24/02/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Designed and implemented `RecruiterShell.tsx` as the master layout for recruiter routes.
- [x] Built the `RecruiterAppSidebar.tsx` for a clean, collapsible navigation menu.
- [x] Created the `DashboardHome.tsx` for a high-level overview of active jobs and total applicants.
- [x] Ensured role-based access control (RBAC) routes correctly redirect users based on their Cognito custom attributes.

---

### Module 8.2: Job Management & Candidate Rankings
* **Date Completed:** 26/02/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `JobCreation.tsx` page for recruiters to input Job Descriptions.
- [x] Built the `CandidateRankings.tsx` component to display a sortable data table of applicants.
- [x] Created the `CandidateReport.tsx` view to show the detailed AI breakdown.
- [x] Connected the UI components to local state management.

**Artifacts:**
- 🖼️ `[recruiter-rankings-dashboard.png]`

---

### Module 8.3: Real-Time GraphQL via AWS AppSync
* **Date Completed:** 28/02/2025
* **Time Spent:** 5.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Set up the `appSyncOperations.ts` library file to define GraphQL queries, mutations, and subscriptions.
- [x] Developed the `useAppSyncSubscription.ts` custom React hook to manage WebSocket connections securely.
- [x] Integrated the subscription hook into `CandidateRankings` for real-time updates.
- [x] Handled AppSync authentication using the Amazon Cognito User Pool tokens from Week 6.

**Artifacts:**
- 📄 `[useAppSyncSubscription.ts]`
- 📄 `[appSyncOperations.ts]`

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully implemented AWS AppSync GraphQL subscriptions — recruiters can watch candidate scores populate in real-time.
* **Next Steps:** Moving into the real-time Interview Workspace (WebRTC, mic volume tracking, and emotion analysis hooks).
