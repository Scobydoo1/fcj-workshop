---
title: "Tuần 8 - Nhật ký Công việc"
date: 2026-02-23
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

# ☁️ Nhật ký Thực tập AWS: Tuần 8 - Recruiter Dashboard & AWS AppSync Thời gian thực

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 23/02/2025 - 01/03/2025  
**Mục tiêu:** Phát triển giao diện Nhà tuyển dụng (Recruiter) để quản lý công việc và triển khai AWS AppSync GraphQL subscriptions để nhận điểm số ứng viên theo thời gian thực từ AI backend.

Khi luồng ứng viên đã hoạt động tốt, tuần này mình chuyển sang phần dành cho Nhà tuyển dụng của SmartHire AI.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 8.1: Layout & Điều hướng cho Nhà tuyển dụng
* **Ngày hoàn thành:** 24/02/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Thiết kế và lập trình `RecruiterShell.tsx` làm layout chính cho các route của nhà tuyển dụng.
- [x] Xây dựng `RecruiterAppSidebar.tsx` sử dụng các component của shadcn/ui để tạo menu điều hướng dạng gập (collapsible).
- [x] Tạo trang `DashboardHome.tsx` để cung cấp cho nhà tuyển dụng cái nhìn tổng quan về các công việc đang mở.
- [x] Đảm bảo phân quyền RBAC hoạt động đúng, tự động điều hướng user dựa trên custom attributes của Cognito.

---

### Bài 8.2: Quản lý Công việc & Bảng xếp hạng Ứng viên
* **Ngày hoàn thành:** 26/02/2025
* **Thời gian thực hiện:** 4.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Phát triển trang `JobCreation.tsx`, cho phép nhà tuyển dụng nhập Mô tả công việc (JD) để gửi tới AI Lambda.
- [x] Xây dựng component `CandidateRankings.tsx` để hiển thị bảng dữ liệu ứng viên có thể sắp xếp (sortable).
- [x] Tạo giao diện `CandidateReport.tsx` hiển thị chi tiết báo cáo AI.
- [x] Kết nối các UI components với state management ở local để chuẩn bị ghép API.

**Tài liệu đính kèm (Artifacts):**
- 🖼️ `[recruiter-rankings-dashboard.png]`
- 📄 `[CandidateRankings.tsx]`

---

### Bài 8.3: GraphQL Thời gian thực với AWS AppSync
* **Ngày hoàn thành:** 28/02/2025
* **Thời gian thực hiện:** 5.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Thiết lập file `appSyncOperations.ts` để định nghĩa các GraphQL queries, mutations, và subscriptions.
- [x] Lập trình custom React hook `useAppSyncSubscription.ts` để quản lý các kết nối WebSocket một cách bảo mật.
- [x] Tích hợp subscription hook vào component `CandidateRankings` để bảng UI tự động cập nhật khi backend tính điểm xong.
- [x] Xử lý xác thực AppSync bằng cách sử dụng token của Amazon Cognito User Pool.

**Khắc phục sự cố / Bài học:**
> Làm việc với GraphQL subscriptions đòi hỏi phải xử lý cẩn thận vòng đời của React component. Mình phải đảm bảo kết nối WebSocket được dọn dẹp sạch sẽ khi component unmount để tránh rò rỉ bộ nhớ.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[useAppSyncSubscription.ts]`
- 📄 `[appSyncOperations.ts]`

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Triển khai thành công AWS AppSync GraphQL subscriptions, tạo ra một UI phản hồi nhanh, nơi nhà tuyển dụng có thể xem điểm số ứng viên tự động nhảy theo thời gian thực.
* **Bước tiếp theo:** Tiến vào module frontend phức tạp nhất: Không gian Phỏng vấn trực tuyến với WebRTC.
