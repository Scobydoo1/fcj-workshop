---
title: "Tuần 7 - Nhật ký Công việc"
date: 2026-02-16
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

# ☁️ Nhật ký Thực tập AWS: Tuần 7 - Candidate Dashboard & Tải lên S3 an toàn

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 16/02/2025 - 22/02/2025  
**Mục tiêu:** Phát triển giao diện (UI shell) cho Ứng viên, triển khai cơ chế tải CV lên sử dụng AWS S3 Pre-signed URLs, và xây dựng giao diện hiển thị các công việc phù hợp.

Sau khi hoàn thiện nền tảng xác thực ở Tuần 6, tuần này được dành hoàn toàn để xây dựng cổng thông tin dành cho ứng viên (Candidate Portal) của SmartHire AI.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 7.1: Giao diện & Điều hướng của Ứng viên
* **Ngày hoàn thành:** 17/02/2025
* **Thời gian thực hiện:** 3.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Lập trình `CandidateLayout.tsx` làm khung giao diện chuẩn cho tất cả các route yêu cầu xác thực của ứng viên.
- [x] Xây dựng `CandidateNavBar.tsx` để điều hướng và hiển thị thông tin profile của user đang đăng nhập.
- [x] Dựng khung trang `CandidateDashboard.tsx` làm trung tâm hiển thị các widget.
- [x] Tích hợp các component cơ bản từ thư viện shadcn/ui để tạo ra giao diện hiện đại, gọn gàng.

---

### Bài 7.2: Widget tải CV & S3 Pre-signed URLs
* **Ngày hoàn thành:** 19/02/2025
* **Thời gian thực hiện:** 4.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Phát triển component `CVUploadWidget.tsx` hỗ trợ kéo thả (drag-and-drop) cho file PDF.
- [x] Thêm hiệu ứng phản hồi giao diện sử dụng component `Progress` của shadcn/ui.
- [x] Tích hợp mô hình AWS S3 Pre-signed URL: Frontend xin một URL tạm thời từ backend, sau đó gọi lệnh `PUT` để đẩy file thẳng lên S3 bucket.
- [x] Cấu hình CORS trên bucket S3 để cho phép nhận request PUT trực tiếp từ domain của frontend.

**Khắc phục sự cố / Bài học:**
> Ban đầu gặp lỗi CORS khi trình duyệt cố gắng upload thẳng lên S3. Mình phải cập nhật lại cấu hình CORS của S3 Bucket để cho phép phương thức `PUT` và hiển thị header `ETag`.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[CVUploadWidget.tsx]`
- 🖼️ `[s3-cors-configuration-rule.json]`

---

### Bài 7.3: Giao diện Công việc phù hợp & Bảng Ứng tuyển
* **Ngày hoàn thành:** 21/02/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Xây dựng component `CandidateJobMatches.tsx` để hiển thị các vị trí được AI gợi ý.
- [x] Lập trình component `MatchScoreGauge.tsx` để trực quan hóa điểm số phù hợp giữa CV và Mô tả công việc.
- [x] Tạo `CandidateApplicationsTable.tsx` để theo dõi các đơn ứng tuyển đang diễn ra.
- [x] Thêm các component `Badge` động để hiển thị trạng thái ứng tuyển.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Triển khai thành công mô hình upload file bảo mật trực tiếp lên S3 trong React, bảo vệ backend khỏi việc phải xử lý các payload lớn.
* **Bước tiếp theo:** Chuyển trọng tâm sang phần nền tảng dành cho Nhà tuyển dụng (Recruiter).
