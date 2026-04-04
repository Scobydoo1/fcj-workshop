---
title: "Week 7 Worklog"
date: 2026-02-16
weight: 7
chapter: false
pre: "<b>1.7. </b>"
---

# ☁️ AWS Training Worklog: Week 7 - Candidate Dashboard & Secure Uploads

**Status:** 🟢 Completed  
**Timeframe:** 16/02/2025 - 22/02/2025  
**Objective:** Develop the Candidate UI shell, implement the CV upload mechanism utilizing AWS S3 pre-signed URLs, and build the job matching interfaces.

With the authentication foundation laid down in Week 6, this week was dedicated to building out the candidate-facing portal for SmartHire AI.

---

## 📅 Daily Task Log

### Module 7.1: Candidate Layout & Navigation
* **Date Completed:** 17/02/2025
* **Time Spent:** 3.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Implemented the `CandidateLayout.tsx` as the main wrapper for all candidate authenticated routes.
- [x] Built the `CandidateNavBar.tsx` to handle user navigation and display the authenticated user's profile info.
- [x] Scoped out the main `CandidateDashboard.tsx` page to act as the central hub for widgets.
- [x] Integrated foundational shadcn/ui components (`Card`, `Button`, `Avatar`).

---

### Module 7.2: CV Upload Widget & S3 Pre-signed URLs
* **Date Completed:** 19/02/2025
* **Time Spent:** 4.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `CVUploadWidget.tsx` component with drag-and-drop support for PDF files.
- [x] Added UI feedback using the `Progress` component from shadcn/ui to show file upload status.
- [x] Integrated the AWS S3 Pre-signed URL pattern for direct-to-S3 uploads.
- [x] Configured CORS on the candidate S3 bucket to accept direct PUT requests from the frontend domain.

**Troubleshooting / Learnings:**
> Initially ran into a CORS error when the browser attempted the direct S3 upload. Had to update the S3 Bucket CORS configuration to explicitly allow `PUT` methods.

**Artifacts:**
- 📄 `[CVUploadWidget.tsx]`
- 🖼️ `[s3-cors-configuration-rule.json]`

---

### Module 7.3: Job Matching & Applications UI
* **Date Completed:** 21/02/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Built the `CandidateJobMatches.tsx` component to display AI-recommended roles.
- [x] Implemented the `MatchScoreGauge.tsx` UI component to visually represent the AI compatibility score.
- [x] Created the `CandidateApplicationsTable.tsx` to track ongoing job applications.
- [x] Added dynamic `Badge` components to indicate application statuses.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Engineered a highly efficient, direct-to-S3 CV upload mechanism using Pre-signed URLs, completely bypassing backend bottlenecks.
* **Next Steps:** Building out the Recruiter portal and integrating AWS AppSync for real-time scoring data.
