---
title: "Week 10 Worklog"
date: 2026-03-09
weight: 10
chapter: false
pre: "<b>1.10. </b>"
---

# ☁️ AWS Training Worklog: Week 10 - CI/CD Pipeline & Final Polish

**Status:** 🟢 Completed  
**Timeframe:** 09/03/2025 - 15/03/2025  
**Objective:** Finalize the frontend UI/UX (including Theme Management), automate the deployment process using GitHub Actions, and conduct end-to-end integration testing.

As the SmartHire AI front-end nears completion, this week was dedicated to operational excellence and user experience.

---

## 📅 Daily Task Log

### Module 10.1: UI/UX Polishing & Theme Management
* **Date Completed:** 10/03/2025
* **Time Spent:** 3.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Implemented the `ThemeContext.ts` and `ThemeProvider.tsx` to manage global UI state.
- [x] Built the `ThemeToggle.tsx` component for seamless Light/Dark/System mode switching.
- [x] Audited all shadcn/ui components to ensure Tailwind color variables adapt correctly to theme changes.
- [x] Cleaned up mobile responsiveness using the `use-mobile.ts` hook.

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
- [x] Set up pipeline steps to automatically run `npm install` and `npm run build` on push to `main`.
- [x] Configured the pipeline to authenticate with AWS using OIDC (OpenID Connect).
- [x] Added an AWS CLI step to sync the `./dist` build folder to the production S3 bucket.

**Troubleshooting / Learnings:**
> Moving from hardcoded IAM keys to an IAM OIDC Identity Provider was a major security upgrade — temporary, short-lived credentials scoped strictly to S3 and CloudFront tasks.

**Artifacts:**
- 📄 `[.github/workflows/deploy.yml]`

---

### Module 10.3: CloudFront Invalidation & AWS Buildspec
* **Date Completed:** 14/03/2025
* **Time Spent:** 3.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Appended a step in GitHub Actions to run `aws cloudfront create-invalidation --paths "/*"`.
- [x] Reviewed the `buildspec.yml` file for AWS CodeBuild integration.
- [x] Tested the full CI/CD lifecycle: pushed a minor UI change and verified it appeared live within 2 minutes.

---

### Module 10.4: End-to-End System Testing
* **Date Completed:** 15/03/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Executed the Candidate Flow: registered, uploaded a CV via S3 pre-signed URLs, and viewed AI-matched jobs.
- [x] Executed the Recruiter Flow: created a job description, tracked real-time AI processing via AppSync, and reviewed rankings.
- [x] Documented minor bugs and created GitHub issues for final sprint resolution.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully automated the deployment pipeline using GitHub Actions, bridging the gap between code commits and live cloud infrastructure.
* **Next Steps:** Project presentation preparation and final code documentation review.
