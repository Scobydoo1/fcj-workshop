---
title: "Week 9 Worklog"
date: 2026-03-02
weight: 9
chapter: false
pre: "<b>1.9. </b>"
---

# ☁️ AWS Training Worklog: Week 9 - Real-Time AI Interview Workspace

**Status:** 🟢 Completed  
**Timeframe:** 02/03/2025 - 08/03/2025  
**Objective:** Architect and implement the real-time Interview Workspace, managing device permissions, media streams, and complex AI interaction states.

This week, I tackled the core feature of the SmartHire platform: the live AI interview environment.

---

## 📅 Daily Task Log

### Module 9.1: Workspace Layout & Device Permissions
* **Date Completed:** 03/03/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `InterviewWorkspace.tsx` as the main orchestrator for the interview session.
- [x] Implemented a 3-panel layout: `LeftPanel` (video feed), `CenterPanel` (code editor), and `RightPanel` (chat/transcript).
- [x] Created the `PermissionsModal.tsx` to handle browser requests for camera and microphone access gracefully.
- [x] Built the `useMediaDevices.ts` hook to enumerate available input devices and manage active media streams.

---

### Module 9.2: Media Streaming & Session State
* **Date Completed:** 05/03/2025
* **Time Spent:** 4.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `useMicVolume.ts` hook using the Web Audio API to create a visual volume indicator.
- [x] Created the `useSessionRecorder.ts` hook to capture the live video/audio feed using the `MediaRecorder` API.
- [x] Implemented `useAIState.ts` to manage the complex state machine of the AI interviewer.
- [x] Built the `EndInterviewModal.tsx` to handle graceful termination and cleanup of the session.

**Artifacts:**
- 📄 `[useMicVolume.ts]`
- 📄 `[useAIState.ts]`

---

### Module 9.3: AI Integrations (Speech, Emotion, Code)
* **Date Completed:** 07/03/2025
* **Time Spent:** 5.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Implemented `useSpeechTranscript.ts` to handle real-time Speech-to-Text conversion.
- [x] Built the `useEmotionAnalysis.ts` hook for facial analysis via the backend `emotion_tracker_lambda`.
- [x] Developed `useCodeRunner.ts` to execute candidate code snippets safely.
- [x] Synchronized all hooks within `InterviewWorkspace` so speech, emotion, and code states are sent collectively.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully engineered a highly complex, state-heavy React environment handling live media streams, visual audio feedback, and multiple asynchronous AI processing hooks simultaneously.
* **Next Steps:** Week 10 — UI/UX polishing, Dark Mode, GitHub Actions CI/CD pipeline, and end-to-end testing.
