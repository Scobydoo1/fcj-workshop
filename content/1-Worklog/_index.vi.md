# ☁️ Nhật ký Thực tập AWS: Tuần 9 - Không gian Phỏng vấn AI Thời gian thực

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 02/03/2025 - 08/03/2025  
**Mục tiêu:** Thiết kế kiến trúc và lập trình Không gian Phỏng vấn (Interview Workspace) theo thời gian thực, quản lý quyền truy cập thiết bị, luồng media và các trạng thái tương tác AI phức tạp.

Tuần này, mình tập trung xử lý tính năng cốt lõi nhất của nền tảng SmartHire: môi trường phỏng vấn AI trực tiếp. Công việc này đòi hỏi phải vượt ra khỏi các thao tác CRUD thông thường để quản lý các luồng dữ liệu liên tục, xử lý thiết bị qua WebRTC, và điều phối đồng thời nhiều hook AI (chuyển đổi giọng nói, theo dõi cảm xúc, và thực thi mã code).

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 9.1: Layout Phỏng vấn & Quyền truy cập Thiết bị
* **Ngày hoàn thành:** 03/03/2025
* **Thời gian thực hiện:** 4.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Lập trình `InterviewWorkspace.tsx` làm component điều phối chính cho toàn bộ phiên phỏng vấn.
- [x] Triển khai layout 3 phần: `LeftPanel` (hiển thị camera), `CenterPanel` (trình soạn thảo code/bảng trắng), và `RightPanel` (khung chat/transcript).
- [x] Tạo `PermissionsModal.tsx` để xử lý mượt mà việc xin quyền truy cập camera và microphone từ trình duyệt trước khi phỏng vấn bắt đầu.
- [x] Xây dựng hook `useMediaDevices.ts` để liệt kê các thiết bị đầu vào khả dụng và quản lý các luồng media đang hoạt động.

**Ghi chú & Quan sát:**
> Xử lý quyền trên trình duyệt khá phức tạp vì người dùng có thể từ chối hoặc gặp lỗi phần cứng. `PermissionsModal` đóng vai trò rào chắn quan trọng để đảm bảo phiên phỏng vấn không thể bắt đầu nếu không lấy được luồng camera/mic cần thiết cho AI phân tích.

---

### Bài 9.2: Truyền phát Media & Trạng thái Phiên (Session)
* **Ngày hoàn thành:** 05/03/2025
* **Thời gian thực hiện:** 4.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Phát triển hook `useMicVolume.ts` sử dụng Web Audio API (`AudioContext` và `AnalyserNode`) để tạo hiệu ứng thanh âm lượng (volume indicator) khi ứng viên đang nói.
- [x] Tạo hook `useSessionRecorder.ts` để ghi lại video/audio trực tiếp bằng `MediaRecorder` API, chuẩn bị cho việc upload file ghi hình lên AWS S3 sau khi kết thúc.
- [x] Lập trình `useAIState.ts` để quản lý cỗ máy trạng thái (state machine) phức tạp của AI phỏng vấn (VD: "Đang nghe", "Đang suy nghĩ", "Đang nói").
- [x] Xây dựng `EndInterviewModal.tsx` để xử lý việc kết thúc phiên và dọn dẹp bộ nhớ gọn gàng.

**Khắc phục sự cố / Bài học:**
> Ban đầu mình phát hiện rò rỉ bộ nhớ (memory leaks) khi chuyển sang trang khác. Mình phải rà soát và đảm bảo mọi track media đều được dừng (`track.stop()`) và `AudioContext` phải đóng bên trong hàm dọn dẹp (cleanup) của `useEffect` trong các hook này.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[useMicVolume.ts]`
- 📄 `[useAIState.ts]`

---

### Bài 9.3: Tích hợp AI (Giọng nói, Cảm xúc, Code)
* **Ngày hoàn thành:** 07/03/2025
* **Thời gian thực hiện:** 5.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Triển khai `useSpeechTranscript.ts` để xử lý chuyển đổi Giọng nói thành Văn bản (chuẩn bị tích hợp Amazon Transcribe).
- [x] Xây dựng hook `useEmotionAnalysis.ts` để chụp khung hình video định kỳ và gửi tới backend `emotion_tracker_lambda` nhằm phân tích nét mặt.
- [x] Phát triển `useCodeRunner.ts` để thực thi các đoạn code của ứng viên một cách an toàn và trả kết quả về giao diện `CenterPanel`.
- [x] Đồng bộ hóa tất cả các hook này bên trong `InterviewWorkspace` để dữ liệu giọng nói, cảm xúc và code được gửi tập trung về orchestrator.

**Ghi chú & Quan sát:**
> Đây là nơi nền tảng thực sự mang lại cảm giác "Trí tuệ nhân tạo". Việc thiết lập thời gian chờ (intervals) để chụp khung hình cảm xúc mà không làm đơ luồng render chính của React là một thử thách. Mình đã phải tối ưu hóa logic trích xuất khung hình để đảm bảo video của ứng viên vẫn hiển thị hoàn toàn mượt mà.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Lập trình thành công một môi trường React độ phức tạp cao, chứa nhiều state, xử lý mượt mà luồng media trực tiếp, phản hồi âm thanh trực quan và chạy song song nhiều hook AI bất đồng bộ mà không làm giảm hiệu suất.
* **Bước tiếp theo:** Chuyển sang Tuần 10, chặng đường cuối cùng! Mình sẽ tập trung đánh bóng giao diện (Dark mode qua `ThemeContext`), hoàn thiện pipeline triển khai tự động CI/CD lên AWS thông qua GitHub Actions, và thực hiện kiểm thử toàn hệ thống (end-to-end testing).
