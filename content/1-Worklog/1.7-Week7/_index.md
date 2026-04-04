# ☁️ AWS Training Worklog: Week 7 - Candidate Dashboard & Secure Uploads

**Status:** 🟢 Completed  
**Timeframe:** 16/02/2025 - 22/02/2025  
**Objective:** Develop the Candidate UI shell, implement the CV upload mechanism utilizing AWS S3 pre-signed URLs, and build the job matching interfaces.

With the authentication foundation laid down in Week 6, this week was dedicated to building out the candidate-facing portal for SmartHire AI. A major technical focus was securely handling resume uploads without bottlenecking an API server by leveraging direct-to-S3 uploads.

---

## 📅 Daily Task Log

### Module 7.1: Candidate Layout & Navigation
* **Date Completed:** 17/02/2025
* **Time Spent:** 3.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Implemented the `CandidateLayout.tsx` as the main wrapper for all candidate authenticated routes.
- [x] Built the `CandidateNavBar.tsx` to handle user navigation and display the authenticated user's profile info from the auth store.
- [x] Scoped out the main `CandidateDashboard.tsx` page to act as the central hub for widgets.
- [x] Integrated foundational shadcn/ui components (`Card`, `Button`, `Avatar`) to establish a clean, modern aesthetic.

**Notes & Observations:**
> Separating the layout from the page content makes route management much cleaner. Using the layout to handle authorization checks ensures that if a user token expires, they are immediately redirected back to the login screen before any sensitive dashboard components mount.

---

### Module 7.2: CV Upload Widget & S3 Pre-signed URLs
* **Date Completed:** 19/02/2025
* **Time Spent:** 4.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `CVUploadWidget.tsx` component with drag-and-drop support for PDF files.
- [x] Added UI feedback using the `Progress` component from shadcn/ui to show file upload status.
- [x] Integrated the AWS S3 Pre-signed URL pattern: The frontend requests a temporary, secure URL from the backend, then `PUT`s the file directly to the S3 bucket.
- [x] Configured CORS (Cross-Origin Resource Sharing) on the candidate S3 bucket to accept direct PUT requests from the frontend domain.

**Troubleshooting / Learnings:**
> Initially ran into a CORS error when the browser attempted the direct S3 upload. I had to update the S3 Bucket CORS configuration to explicitly allow `PUT` methods and expose the `ETag` header. This pattern is highly efficient because it completely bypasses the backend compute tier for heavy file transfers.

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
- [x] Implemented the `MatchScoreGauge.tsx` UI component to visually represent the AI compatibility score between the user's CV and the Job Description.
- [x] Created the `CandidateApplicationsTable.tsx` using the shadcn/ui `Table` component to track ongoing job applications.
- [x] Added dynamic `Badge` components to indicate application statuses (e.g., "Pending", "Reviewed
