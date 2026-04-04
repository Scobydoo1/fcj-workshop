# ☁️ Nhật ký Thực tập AWS: Tuần 1 - Nền tảng Cốt lõi

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 05/01/2025 - 11/01/2025  
**Mục tiêu:** Thiết lập môi trường AWS nền tảng an toàn, có giám sát và nắm vững quản lý định danh để chuẩn bị cho việc triển khai hạ tầng cloud sắp tới.

Tài liệu này đóng vai trò là nhật ký công việc (worklog) chi tiết cho Tuần 1. Nó theo dõi tiến độ hàng ngày, các cấu hình đã áp dụng và những khó khăn đã giải quyết trong quá trình xây dựng nền tảng kiến thức hạ tầng AWS.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 1.1: Thiết lập & Khởi tạo Tài khoản
* **Ngày hoàn thành:** 05/01/2025
* **Thời gian thực hiện:** 1.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Đăng ký tài khoản AWS Free Tier mới.
- [x] Bảo mật tài khoản Root (Bật MFA, tạo mật khẩu mạnh).
- [x] Khám phá giao diện AWS Management Console và các Region (Khu vực).

**Ghi chú & Quan sát:**
> Đã thiết lập Region mặc định là `ap-southeast-1` (Singapore) để tối ưu độ trễ. Môi trường này sau này sẽ là nền tảng để host các frontend React và microservices Java Spring Boot, nên việc thiết lập bảo mật cơ bản từ đầu là rất quan trọng.

---

### Bài 1.2: Quản lý Chi phí (AWS Budgets)
* **Ngày hoàn thành:** 06/01/2025
* **Thời gian thực hiện:** 2.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Truy cập AWS Billing Dashboard (Bảng điều khiển thanh toán).
- [x] Tạo ngân sách Zero-Spend (Ngân sách 0 đồng) để theo dõi giới hạn Free Tier.
- [x] Cấu hình hệ thống cảnh báo gửi về email khi dự báo chi phí vượt quá $0.01.

**Khắc phục sự cố / Bài học:**
> Có một chút độ trễ (khoảng 24 giờ) để dữ liệu thanh toán cập nhật trên dashboard sau khi tạo tài khoản. Đã cấu hình các cảnh báo để đảm bảo không có chi phí phát sinh bất ngờ trong quá trình testing.

**Tài liệu đính kèm (Artifacts):**
- 🖼️ `[budget-alert-config-20250106.png]`

---

### Bài 1.3: Sử dụng AWS Support
* **Ngày hoàn thành:** 08/01/2025
* **Thời gian thực hiện:** 0.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tìm hiểu các Gói hỗ trợ AWS (Basic, Developer, Business, Enterprise).
- [x] Thao tác trên giao diện Support Center.
- [x] Đọc tài liệu về cách trình bày câu hỏi kỹ thuật chuẩn xác để được hỗ trợ nhanh nhất.

**Điểm cốt lõi rút ra:**
> Hiện tại đang dùng gói Basic, đủ để giải quyết các thắc mắc về tài khoản và thanh toán. Tuy nhiên, để được hỗ trợ kỹ thuật chuyên sâu về kiến trúc sau này, cần nâng cấp lên ít nhất là gói Developer hoặc Business.

---

### Bài 1.4: Bảo mật & Định danh (AWS IAM)
* **Ngày hoàn thành:** 10/01/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tạo IAM Admin User cho các tác vụ hàng ngày (không dùng tài khoản Root nữa).
- [x] Bật MFA cho tài khoản IAM user mới qua ứng dụng xác thực.
- [x] Tạo IAM Group (`DevOps-Admins`) và gán chính sách `AdministratorAccess`.
- [x] Tạo và lưu trữ an toàn Access Keys để dùng cho AWS CLI sau này.
- [x] Đăng nhập thông qua đường dẫn dành riêng cho IAM User.

**Khó khăn & Cách giải quyết:**
> Đã dành thời gian nghiên cứu kỹ các IAM roles và policies để hiểu về nguyên tắc quyền tối thiểu (least privilege). Điều này sẽ rất hữu ích khi cấu hình IAM roles cho các hệ thống như AWS Sentinel (phát hiện bất thường log) để truy cập an toàn vào CloudWatch và S3 mà không cần hardcode thông tin đăng nhập.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[admin-group-policy-trust.json]`
- 🖼️ `[iam-security-hub-green.png]`

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Đã khóa an toàn tài khoản Root, thiết lập các rào chắn kiểm soát chi phí, và tạo thành công tài khoản quản trị IAM an toàn để phục vụ công việc phát triển hàng ngày.
* **Các khái niệm cần ôn tập lại:** Cần tìm hiểu sâu hơn về cấu trúc JSON của IAM Policy (các block Condition, ARNs tài nguyên cụ thể) để có thể giới hạn quyền truy cập chặt chẽ hơn cho các role ứng dụng cụ thể.
