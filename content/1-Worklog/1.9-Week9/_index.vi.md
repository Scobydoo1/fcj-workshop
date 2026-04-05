---
title: "Tuần 9 - Nhật ký Công việc"
date: 2026-03-02
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

# ☁️ Nhật ký Thực tập AWS: Tuần 9 - Không gian Phỏng vấn AI Thời gian thực

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 02/03/2025 - 08/03/2025  
**Mục tiêu:** Thiết kế kiến trúc và lập trình Không gian Phỏng vấn (Interview Workspace) theo thời gian thực, quản lý quyền truy cập thiết bị, luồng media và các trạng thái tương tác AI phức tạp.

Tuần này, mình tập trung xử lý tính năng cốt lõi nhất của nền tảng SmartHire: môi trường phỏng vấn AI trực tiếp.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 9.1: Layout Phỏng vấn & Quyền truy cập Thiết bị
* **Ngày hoàn thành:** 03/03/2025
* **Thời gian thực hiện:** 4.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Lập trình `InterviewWorkspace.tsx` làm component điều phối chính cho toàn bộ phiên phỏng vấn.
- [x] Triển khai layout 3 phần: `LeftPanel` (hiển thị camera), `CenterPanel` (trình soạn thảo code), và `RightPanel` (khung chat/transcript).
- [x] Tạo `PermissionsModal.tsx` để xử lý việc xin quyền truy cập camera và microphone từ trình duyệt.
- [x] Xây dựng hook `useMediaDevices.ts` để liệt kê các thiết bị đầu vào khả dụng và quản lý các luồng media.

---

### Bài 9.2: Truyền phát Media & Trạng thái Phiên (Session)
* **Ngày hoàn thành:** 05/03/2025
* **Thời gian thực hiện:** 4.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Phát triển hook `useMicVolume.ts` sử dụng Web Audio API để tạo hiệu ứng thanh âm lượng khi ứng viên đang nói.
- [x] Tạo hook `useSessionRecorder.ts` để ghi lại video/audio trực tiếp bằng `MediaRecorder` API.
- [x] Lập trình `useAIState.ts` để quản lý cỗ máy trạng thái phức tạp của AI phỏng vấn.
- [x] Xây dựng `EndInterviewModal.tsx` để xử lý việc kết thúc phiên và dọn dẹp bộ nhớ.

**Khắc phục sự cố / Bài học:**
> Ban đầu phát hiện rò rỉ bộ nhớ khi chuyển sang trang khác. Mình phải đảm bảo mọi track media đều được dừng và `AudioContext` phải đóng bên trong hàm dọn dẹp của `useEffect`.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[useMicVolume.ts]`
- 📄 `[useAIState.ts]`

---

### Bài 9.3: Tích hợp AI (Giọng nói, Cảm xúc, Code)
* **Ngày hoàn thành:** 07/03/2025
* **Thời gian thực hiện:** 5.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Triển khai `useSpeechTranscript.ts` để xử lý chuyển đổi Giọng nói thành Văn bản (Amazon Transcribe).
- [x] Xây dựng hook `useEmotionAnalysis.ts` để chụp khung hình video định kỳ và gửi tới backend phân tích nét mặt.
- [x] Phát triển `useCodeRunner.ts` để thực thi các đoạn code của ứng viên một cách an toàn.
- [x] Đồng bộ hóa tất cả các hook bên trong `InterviewWorkspace` để dữ liệu giọng nói, cảm xúc và code được gửi tập trung về orchestrator.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Lập trình thành công một môi trường React độ phức tạp cao, xử lý mượt mà luồng media trực tiếp và chạy song song nhiều hook AI bất đồng bộ.
* **Bước tiếp theo:** Chuyển sang Tuần 10 — tập trung đánh bóng giao diện (Dark mode), hoàn thiện pipeline CI/CD và kiểm thử toàn hệ thống.
