# ☁️ AWS Training Worklog: Week 8 - Recruiter Dashboard & Real-Time AppSync

**Status:** 🟢 Completed  
**Timeframe:** 23/02/2025 - 01/03/2025  
**Objective:** Develop the Recruiter interface for job management and implement AWS AppSync GraphQL subscriptions to receive real-time candidate scoring updates from the AI backend.

With the Candidate flow functioning, this week I pivoted to the Recruiter side of SmartHire AI. The main challenge was ensuring that recruiters don't have to manually refresh the page to see when a candidate's CV has been processed by our AI Lambdas. To solve this, I integrated AWS AppSync to push real-time updates to the React client via WebSockets.

---

## 📅 Daily Task Log

### Module 8.1: Recruiter Layout & Navigation
* **Date Completed:** 24/02/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Designed and implemented `RecruiterShell.tsx` to serve as the master layout for recruiter routes.
- [x] Built the `RecruiterAppSidebar.tsx` utilizing shadcn/ui components for a clean, collapsible navigation menu.
- [x] Created the `DashboardHome.tsx` to give recruiters a high-level overview of active jobs and total applicants.
- [x] Ensured role-based access control (RBAC) routes correctly redirect users based on their Cognito custom attributes.

**Notes & Observations:**
> The recruiter interface needs to be heavily data-dense compared to the candidate UI. Using a sidebar layout instead of a top navbar provides much more horizontal screen real estate for data tables and AI reports.

---

### Module 8.2: Job Management & Candidate Rankings
* **Date Completed:** 26/02/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `JobCreation.tsx` page, allowing recruiters to input Job Descriptions (JDs) which will be sent to our `jd_parser` AI Lambda.
- [x] Built the `CandidateRankings.tsx` component to display a sortable data table of applicants.
- [x] Created the `CandidateReport.tsx` view to show the detailed AI breakdown (skills matched, missing keywords, experience evaluation).
- [x] Connected the UI components to local state management to prepare for API integration.

**Artifacts:**
- 🖼️ `[recruiter-rankings-dashboard.png]`
- 📄 `[CandidateRankings.tsx]`

---

### Module 8.3: Real-Time GraphQL via AWS AppSync
* **Date Completed:** 28/02/2025
* **Time Spent:** 5.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Set up the `appSyncOperations.ts` library file to define the GraphQL queries, mutations, and subscriptions based on the `appsync_schema.graphql` definition.
- [x] Developed the `useAppSyncSubscription.ts` custom React hook to manage WebSocket connections securely.
- [x] Integrated the subscription hook into the `CandidateRankings` component so that when the AWS Step Functions backend finishes scoring a candidate, the frontend UI table updates instantly.
- [x] Handled AppSync authentication using the Amazon Cognito User Pool tokens established in Week 6.

**Troubleshooting / Learnings:**
> Working with GraphQL subscriptions required careful handling of the React component lifecycle. I had to ensure the WebSocket connection in `useAppSyncSubscription.ts` properly cleans up (unsubscribes) when the component unmounts to prevent memory leaks and duplicate data rendering. 

**Artifacts:**
- 📄 `[useAppSyncSubscription.ts]`
- 📄 `[appSyncOperations.ts]`

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully implemented AWS AppSync GraphQL subscriptions, creating a reactive UI where recruiters can watch candidate scores populate in real-time as the AI backend processes the CVs.
* **Next Steps:** Moving into the most complex frontend module: the real-time Interview Workspace (WebRTC, mic volume tracking, and emotion analysis hooks).
