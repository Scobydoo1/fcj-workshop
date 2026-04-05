---
title: "Tuần 6 - Nhật ký Công việc"
date: 2026-02-09
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

# ☁️ Nhật ký Thực tập AWS: Tuần 6 - Khởi động Dự án SmartHire & AWS Auth

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 09/02/2025 - 15/02/2025  
**Mục tiêu:** Khởi tạo kiến trúc front-end cho SmartHire AI, cấu hình lưu trữ tĩnh trên cloud và tích hợp Amazon Cognito để xác thực bảo mật cho ứng viên và nhà tuyển dụng.

Tuần này đánh dấu sự chuyển giao từ việc học nền tảng AWS sang phát triển dự án thực tế. Mình đã chính thức bắt tay vào làm front-end cho **SmartHire**, nền tảng tuyển dụng tích hợp AI. Trọng tâm của tuần này là dựng khung (scaffold) ứng dụng React và kết nối hệ thống xác thực cloud-native.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 6.1: Khởi tạo Front-end & Cấu hình Hosting AWS
* **Ngày hoàn thành:** 10/02/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Khởi tạo repository front-end `SmartHire-AI-dev` sử dụng Vite, React và TypeScript.
- [x] Cấu hình Tailwind CSS và cấu trúc routing cơ bản cho các giao diện Guest, Candidate và Recruiter.
- [x] Cấp phát một Amazon S3 bucket chuyên dụng để lưu trữ các file build production.
- [x] Thiết lập Amazon CloudFront distribution trỏ đến S3 origin nhằm đảm bảo tốc độ tải trang nhanh và bảo mật HTTPS.

**Ghi chú & Quan sát:**
> Việc dùng Vite giúp tăng tốc độ phát triển local lên rất nhiều. Về phía cloud, đặt CloudFront trước S3 là một phương pháp bảo mật quan trọng, cho phép mình giữ S3 bucket ở chế độ private (dùng Origin Access Control) mà vẫn phân phối web app an toàn đến người dùng.

---

### Bài 6.2: Quản lý Định danh (Thiết lập Amazon Cognito)
* **Ngày hoàn thành:** 12/02/2025
* **Thời gian thực hiện:** 4.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tạo một Amazon Cognito User Pool mới dành riêng cho ứng dụng SmartHire.
- [x] Cấu hình các thuộc tính người dùng tùy chỉnh (custom attributes) để phân biệt giữa role `Candidate` và `Recruiter`.
- [x] Thiết lập chính sách mật khẩu và bật tính năng xác minh email cho các tài khoản mới đăng ký.
- [x] Tạo Cognito App Clients và ghi chú lại các Client ID để đưa vào biến môi trường của front-end.

**Khắc phục sự cố / Bài học:**
> Mình đã phải nghiên cứu kỹ cách Cognito xử lý các custom claims. Việc đảm bảo role của người dùng được gắn thẳng vào JWT token khi login sẽ giúp việc phân quyền routing trên React sau này dễ dàng hơn nhiều.

---

### Bài 6.3: Xây dựng Components Xác thực trên React
* **Ngày hoàn thành:** 14/02/2025
* **Thời gian thực hiện:** 4.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Lập trình `AuthLayout.tsx` để quản lý UI shell cho các màn hình đăng nhập và đăng ký.
- [x] Tạo các custom React hooks (`useAuthLogin.ts`, `useAuthRegister.ts`) để đóng gói logic gọi AWS Cognito SDK.
- [x] Xây dựng các component `Login.tsx` và `Register.tsx`, hoàn thiện với tính năng validate và xử lý lỗi.
- [x] Triển khai wrapper `ProtectedRoute` để chặn các lượt truy cập chưa xác thực vào các route dashboard.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[useAuthLogin.ts]`
- 🖼️ `[smarthire-login-ui-20250214.png]`

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Kết nối thành công dự án React ở local với AWS bằng cách triển khai hoàn chỉnh luồng xác thực bảo mật, sao lưu bởi hệ thống cloud Amazon Cognito.
* **Bước tiếp theo:** Chuyển sang xây dựng giao diện Dashboard cho Candidate và Recruiter, chuẩn bị kết nối front-end với AWS AppSync để nhận dữ liệu thời gian thực.
