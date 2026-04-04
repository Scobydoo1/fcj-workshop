# ☁️ AWS Training Worklog: Week 10 - CI/CD Pipeline & Final Polish

**Status:** 🟢 Completed  
**Timeframe:** 09/03/2025 - 15/03/2025  
**Objective:** Finalize the frontend UI/UX (including Theme Management), automate the deployment process using GitHub Actions, and conduct end-to-end integration testing.

As the SmartHire AI front-end nears completion, this week was dedicated to operational excellence and user experience. Instead of deploying manually, I focused on building a robust Continuous Integration and Continuous Deployment (CI/CD) pipeline to automatically push code changes to our AWS environment.

---

## 📅 Daily Task Log

### Module 10.1: UI/UX Polishing & Theme Management
* **Date Completed:** 10/03/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Implemented the `ThemeContext.ts` and `ThemeProvider.tsx` to manage global UI state.
- [x] Built the `ThemeToggle.tsx` component, allowing users to seamlessly switch between Light, Dark, and System default modes.
- [x] Audited all shadcn/ui components across Candidate and Recruiter dashboards to ensure Tailwind color variables (`bg-background`, `text-foreground`) adapt correctly to theme changes.
- [x] Cleaned up mobile responsiveness using the `use-mobile.ts` hook.

**Notes & Observations:**
> Providing a built-in Dark Mode is a standard requirement for modern web applications. Utilizing Tailwind's CSS variables alongside React Context made the implementation clean and highly performant without unnecessary re-renders.

**Artifacts:**
- 📄 `[ThemeProvider.tsx]`
- 📄 `[ThemeToggle.tsx]`

---

### Module 10.2: GitHub Actions CI/CD Setup
* **Date Completed:** 12/03/2025
* **Time Spent:** 4.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Created the `.github/workflows/deploy.yml` configuration file.
- [x] Set up pipeline steps to automatically run `npm install` and `npm run build` using the Vite bundler whenever code is pushed to the `main` or `dev` branches.
- [x] Configured the pipeline to securely authenticate with AWS using OIDC (OpenID Connect) to avoid storing long-lived IAM access keys in GitHub Secrets.
- [x] Added an AWS CLI step to sync the `./dist` build folder to the production S3 bucket.

**Troubleshooting / Learnings:**
> Moving from hardcoded IAM keys to an IAM OIDC Identity Provider for GitHub Actions was a major security upgrade. It grants temporary, short-lived credentials strictly scoped to the S3 upload and CloudFront invalidation tasks.

**Artifacts:**
- 📄 `[.github/workflows/deploy.yml]`

---

### Module 10.3: CloudFront Invalidation & AWS Buildspec
* **Date Completed:** 14/03/2025
* **Time Spent:** 3.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Appended a step in the GitHub Actions workflow to run `aws cloudfront create-invalidation --paths "/*"`.
- [x] Reviewed the `buildspec.yml` file for potential parallel integration with AWS CodeBuild for backend/infrastructure pipelines.
- [x] Tested the full CI/CD lifecycle: Pushed a minor UI text change to GitHub and verified it appeared live on the production domain within 2 minutes.

**Notes & Observations:**
> The CloudFront invalidation step is critical. Because CloudFront caches the static website files at edge locations globally, simply updating S3 isn't enough. The invalidation forces the CDN to fetch the newly built `index.html` and JavaScript chunks.

---

### Module 10.4: End-to-End System Testing
* **Date Completed:** 15/03/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Executed the Candidate Flow: Registered an account, securely uploaded a CV via S3 pre-signed URLs, and viewed AI-matched jobs.
- [x] Executed the Recruiter Flow: Created a job description, tracked the real-time AI processing via AppSync GraphQL, and reviewed candidate rankings.
- [x] Documented minor bugs and created GitHub issues for final sprint resolution.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully automated the deployment pipeline using GitHub Actions, bridging the gap between code commits and live cloud infrastructure.
* **Next Steps:** Project presentation preparation and final code documentation review.
