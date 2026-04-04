# ☁️ Nhật ký Thực tập AWS: Tuần 10 - Pipeline CI/CD & Hoàn thiện Cuối cùng

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 09/03/2025 - 15/03/2025  
**Mục tiêu:** Hoàn thiện giao diện UI/UX (bao gồm Quản lý Theme), tự động hóa quy trình triển khai bằng GitHub Actions và kiểm thử tích hợp toàn bộ hệ thống (End-to-End).

Khi phần front-end của SmartHire AI gần hoàn tất, tuần này được dành riêng cho việc tối ưu hóa vận hành và trải nghiệm người dùng. Thay vì deploy thủ công, mình tập trung xây dựng một pipeline CI/CD (Tích hợp & Triển khai liên tục) mạnh mẽ để tự động đẩy code lên môi trường AWS.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 10.1: Tinh chỉnh UI/UX & Quản lý Theme
* **Ngày hoàn thành:** 10/03/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Triển khai `ThemeContext.ts` và `ThemeProvider.tsx` để quản lý trạng thái UI toàn cục.
- [x] Xây dựng component `ThemeToggle.tsx`, cho phép người dùng chuyển đổi mượt mà giữa chế độ Sáng (Light), Tối (Dark) và Mặc định theo hệ thống.
- [x] Kiểm tra lại tất cả các component shadcn/ui trên cả hai dashboard để đảm bảo các biến màu của Tailwind (`bg-background`, `text-foreground`) phản hồi chuẩn xác khi đổi theme.
- [x] Tối ưu hóa giao diện trên thiết bị di động (mobile responsiveness) sử dụng hook `use-mobile.ts`.

**Ghi chú & Quan sát:**
> Việc cung cấp sẵn Dark Mode là một yêu cầu tiêu chuẩn cho các ứng dụng web hiện đại. Kết hợp các biến CSS của Tailwind với React Context giúp việc triển khai rất gọn gàng và đạt hiệu suất cao, không gây render lại (re-render) không cần thiết.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[ThemeProvider.tsx]`
- 📄 `[ThemeToggle.tsx]`

---

### Bài 10.2: Thiết lập GitHub Actions CI/CD
* **Ngày hoàn thành:** 12/03/2025
* **Thời gian thực hiện:** 4.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tạo file cấu hình `.github/workflows/deploy.yml`.
- [x] Cài đặt các bước (steps) trong pipeline để tự động chạy `npm install` và `npm run build` bằng Vite mỗi khi có code push lên nhánh `main` hoặc `dev`.
- [x] Cấu hình pipeline xác thực an toàn với AWS thông qua OIDC (OpenID Connect) để tránh việc phải lưu trữ IAM access keys dài hạn trên GitHub Secrets.
- [x] Thêm lệnh AWS CLI để đồng bộ thư mục build `./dist` lên bucket S3 môi trường production.

**Khắc phục sự cố / Bài học:**
> Chuyển từ việc hardcode IAM keys sang dùng IAM OIDC Identity Provider cho GitHub Actions là một bước tiến lớn về bảo mật. Nó cấp các thông tin xác thực tạm thời, thời hạn ngắn, chỉ có quyền truy cập đúng vào tác vụ tải lên S3 và vô hiệu hóa (invalidation) CloudFront.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[.github/workflows/deploy.yml]`

---

### Bài 10.3: CloudFront Invalidation & AWS Buildspec
* **Ngày hoàn thành:** 14/03/2025
* **Thời gian thực hiện:** 3.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Thêm một bước vào workflow GitHub Actions để chạy lệnh `aws cloudfront create-invalidation --paths "/*"`.
- [x] Xem xét file `buildspec.yml` để đánh giá khả năng tích hợp song song với AWS CodeBuild cho các pipeline liên quan đến backend/hạ tầng.
- [x] Kiểm thử toàn bộ vòng đời CI/CD: Thử push một thay đổi nhỏ về text trên UI lên GitHub và xác nhận thay đổi đó xuất hiện trực tiếp trên domain production trong vòng 2 phút.

**Ghi chú & Quan sát:**
> Bước CloudFront invalidation (vô hiệu hóa bộ nhớ đệm) là cực kỳ quan trọng. Vì CloudFront lưu trữ (cache) các file tĩnh ở các edge locations toàn cầu, việc chỉ cập nhật trên S3 là chưa đủ. Lệnh invalidation ép CDN phải tải lại file `index.html` và các cục JavaScript mới vừa build.

---

### Bài 10.4: Kiểm thử Hệ thống (End-to-End Testing)
* **Ngày hoàn thành:** 15/03/2025
* **Thời gian thực hiện:** 4.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Chạy thử luồng Ứng viên: Đăng ký tài khoản, tải CV bảo mật qua S3 pre-signed URLs, và xem các công việc được AI gợi ý.
- [x] Chạy thử luồng Nhà tuyển dụng: Tạo mô tả công việc, theo dõi tiến trình xử lý AI theo thời gian thực qua AppSync GraphQL, và xem bảng xếp hạng ứng viên.
- [x] Ghi chép lại các lỗi nhỏ (bugs) và tạo các GitHub issues để giải quyết trong đợt sprint cuối.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Tự động hóa thành công pipeline triển khai bằng GitHub Actions, kết nối trơn tru quá trình commit code ở local với hệ thống hạ tầng cloud thực tế.
* **Bước tiếp theo:** Chuẩn bị báo cáo tổng kết dự án và rà soát lại toàn bộ tài liệu source code.
