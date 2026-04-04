# ☁️ AWS Training Worklog: Week 9 - Real-Time AI Interview Workspace

**Status:** 🟢 Completed  
**Timeframe:** 02/03/2025 - 08/03/2025  
**Objective:** Architect and implement the real-time Interview Workspace, managing device permissions, media streams, and complex AI interaction states.

This week, I tackled the core feature of the SmartHire platform: the live AI interview environment. This required moving beyond standard CRUD operations into managing continuous data streams, WebRTC device handling, and coordinating multiple simultaneous AI hooks (speech-to-text, emotion tracking, and code execution).

---

## 📅 Daily Task Log

### Module 9.1: Workspace Layout & Device Permissions
* **Date Completed:** 03/03/2025
* **Time Spent:** 4.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `InterviewWorkspace.tsx` as the main orchestrator for the interview session.
- [x] Implemented a 3-panel layout: `LeftPanel` (video feed), `CenterPanel` (code editor/whiteboard), and `RightPanel` (chat/transcript).
- [x] Created the `PermissionsModal.tsx` to handle browser requests for camera and microphone access gracefully before the interview starts.
- [x] Built the `useMediaDevices.ts` hook to enumerate available input devices and manage the active media streams.

**Notes & Observations:**
> Handling browser permissions is tricky because users can deny them or have hardware issues. The `PermissionsModal` is crucial here to ensure a hard stop if we cannot secure the media streams required for the AI to analyze the candidate.

---

### Module 9.2: Media Streaming & Session State
* **Date Completed:** 05/03/2025
* **Time Spent:** 4.5 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Developed the `useMicVolume.ts` hook using the Web Audio API (`AudioContext` and `AnalyserNode`) to create a visual volume indicator when the candidate is speaking.
- [x] Created the `useSessionRecorder.ts` hook to capture the live video/audio feed using the `MediaRecorder` API, preparing it for upload to AWS S3 after the interview.
- [x] Implemented `useAIState.ts` to manage the complex state machine of the AI interviewer (e.g., "Listening", "Thinking", "Speaking").
- [x] Built the `EndInterviewModal.tsx` to handle the graceful termination and cleanup of the session.

**Troubleshooting / Learnings:**
> I noticed memory leaks initially when switching away from the interview page. I had to strictly ensure that all media tracks are stopped (`track.stop()`) and the `AudioContext` is closed within the `useEffect` cleanup functions of these hooks.

**Artifacts:**
- 📄 `[useMicVolume.ts]`
- 📄 `[useAIState.ts]`

---

### Module 9.3: AI Integrations (Speech, Emotion, Code)
* **Date Completed:** 07/03/2025
* **Time Spent:** 5.0 hours
* **Status:** [ ] To Do | [ ] In Progress | [x] Done

**Work Performed:**
- [x] Implemented `useSpeechTranscript.ts` to handle real-time Speech-to-Text conversion (preparing for Amazon Transcribe integration).
- [x] Built the `useEmotionAnalysis.ts` hook, which captures video frames at intervals to be sent to the backend `emotion_tracker_lambda` for facial analysis.
- [x] Developed `useCodeRunner.ts` to execute candidate code snippets safely and return outputs to the `CenterPanel` interface.
- [x] Synchronized these hooks within the `InterviewWorkspace` so that speech, emotion data, and code states are sent collectively to the orchestrator.

**Notes & Observations:**
> This is where the platform truly feels like "AI." Coordinating the intervals for emotion frame capturing without blocking the main React render thread was a challenge. I had to optimize the frame extraction logic to ensure the video feed remains perfectly smooth for the candidate.

---

## 📝 End of Week Summary
* **Biggest achievement this week:** Successfully engineered a highly complex, state-heavy React environment that handles live media streams, visual audio feedback, and multiple asynchronous AI processing hooks simultaneously without performance degradation.
* **Next Steps:** Moving to Week 10, the final stretch! I will focus on UI/UX polishing across the app (Dark mode via `ThemeContext`), finalizing the AWS CI/CD deployment pipeline via GitHub Actions, and performing end-to-end testing.
