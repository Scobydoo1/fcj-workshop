# ☁️ Nhật ký Thực tập AWS: Tuần 7 - Candidate Dashboard & Tải lên S3 an toàn

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 16/02/2025 - 22/02/2025  
**Mục tiêu:** Phát triển giao diện (UI shell) cho Ứng viên, triển khai cơ chế tải CV lên sử dụng AWS S3 Pre-signed URLs, và xây dựng giao diện hiển thị các công việc phù hợp.

Sau khi hoàn thiện nền tảng xác thực ở Tuần 6, tuần này được dành hoàn toàn để xây dựng cổng thông tin dành cho ứng viên (Candidate Portal) của SmartHire AI. Trọng tâm kỹ thuật chính là xử lý việc tải lên hồ sơ (CV) một cách bảo mật mà không làm nghẽn server API, thông qua phương pháp tải trực tiếp lên S3.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 7.1: Giao diện & Điều hướng của Ứng viên
* **Ngày hoàn thành:** 17/02/2025
* **Thời gian thực hiện:** 3.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Lập trình `CandidateLayout.tsx` làm khung giao diện chuẩn cho tất cả các route yêu cầu xác thực của ứng viên.
- [x] Xây dựng `CandidateNavBar.tsx` để điều hướng và hiển thị thông tin profile của user đang đăng nhập (lấy từ auth store).
- [x] Dựng khung trang `CandidateDashboard.tsx` làm trung tâm hiển thị các widget.
- [x] Tích hợp các component cơ bản từ thư viện shadcn/ui (`Card`, `Button`, `Avatar`) để tạo ra giao diện hiện đại, gọn gàng.

**Ghi chú & Quan sát:**
> Việc tách biệt layout khỏi nội dung trang giúp quản lý route sạch sẽ hơn rất nhiều. Sử dụng layout để kiểm tra quyền truy cập (authorization) đảm bảo rằng nếu token hết hạn, người dùng sẽ bị đẩy về trang login ngay lập tức trước khi các component nhạy cảm kịp render.

---

### Bài 7.2: Widget tải CV & S3 Pre-signed URLs
* **Ngày hoàn thành:** 19/02/2025
* **Thời gian thực hiện:** 4.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Phát triển component `CVUploadWidget.tsx` hỗ trợ kéo thả (drag-and-drop) cho file PDF.
- [x] Thêm hiệu ứng phản hồi giao diện sử dụng component `Progress` của shadcn/ui để báo cáo tiến độ tải file.
- [x] Tích hợp mô hình AWS S3 Pre-signed URL: Frontend xin một URL tạm thời, có mã hóa bảo mật từ backend, sau đó gọi lệnh `PUT` để đẩy file thẳng lên S3 bucket.
- [x] Cấu hình CORS (Cross-Origin Resource Sharing) trên bucket S3 chứa CV để cho phép nhận request PUT trực tiếp từ domain của frontend.

**Khắc phục sự cố / Bài học:**
> Ban đầu mình gặp lỗi CORS khi trình duyệt cố gắng upload thẳng lên S3. Mình phải cập nhật lại cấu hình CORS của S3 Bucket để cho phép phương thức `PUT` và hiển thị header `ETag`. Mô hình này cực kỳ tối ưu vì nó giúp các luồng truyền file nặng hoàn toàn bỏ qua tầng compute của backend.

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
- [x] Lập trình component `MatchScoreGauge.tsx` để trực quan hóa điểm số phù hợp (AI compatibility score) giữa CV của người dùng và Mô tả công việc (JD).
- [x] Tạo `CandidateApplicationsTable.tsx` dùng component `Table` của shadcn/ui để theo dõi các đơn ứng tuyển đang diễn ra.
- [x] Thêm các component `Badge` động để hiển thị trạng thái ứng tuyển (VD: "Pending", "Reviewed", "Interview Scheduled").

**Ghi chú & Quan sát:**
> `MatchScoreGauge` là một phần phản hồi cực kỳ quan trọng cho người dùng. Hiện tại nó đang dùng dữ liệu giả (mock data), nhưng cấu trúc đã sẵn sàng để nhận điểm số theo thời gian thực từ AppSync/GraphQL subscriptions sẽ được triển khai trong vài tuần tới.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Triển khai thành công mô hình upload file bảo mật trực tiếp lên S3 trong React, bảo vệ backend khỏi việc phải xử lý các payload lớn, đồng thời mang lại trải nghiệm mượt mà cho ứng viên khi tải CV.
* **Bước tiếp theo:** Chuyển trọng tâm sang phần nền tảng dành cho Nhà tuyển dụng (Recruiter)—xây dựng form tạo công việc, bảng xếp hạng ứng viên và thiết lập GraphQL để cập nhật tiến trình xử lý của AI theo thời gian thực.
