---
title: "Tuần 2 - Nhật ký Công việc"
date: 2026-01-12
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

# ☁️ Nhật ký Thực tập AWS: Tuần 2 - Nền tảng Mạng & Máy chủ tính toán

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 12/01/2025 - 18/01/2025  
**Mục tiêu:** Thiết kế kiến trúc mạng đám mây tùy chỉnh và triển khai các máy chủ ảo để lưu trữ ứng dụng.

Tài liệu này theo dõi tiến độ Tuần 2. Sau khi bảo mật tài khoản ở Tuần 1, tuần này tập trung vào việc cung cấp cấu trúc mạng cốt lõi và tài nguyên tính toán cần thiết cho việc triển khai ứng dụng.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 2.1: Hạ tầng Mạng (Amazon VPC)
* **Ngày hoàn thành:** 13/01/2025
* **Thời gian thực hiện:** 4.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tạo một Virtual Private Cloud (VPC) tùy chỉnh từ đầu.
- [x] Cấu hình Public và Private Subnet trên hai Availability Zone để đảm bảo tính sẵn sàng cao (High Availability).
- [x] Triển khai Internet Gateway (IGW) và cấu hình Route Table để định tuyến cho public subnet.
- [x] Thiết lập NAT Gateway để cho phép các private subnet tải xuống các bản cập nhật một cách an toàn.

**Ghi chú & Quan sát:**
> Việc thiết kế phân chia public/private subnet rất quan trọng. Mục tiêu là sau này sẽ đặt các frontend React giao tiếp với người dùng ở public subnet (hoặc qua CloudFront), trong khi vẫn giữ các dịch vụ backend Java Spring Boot được cách ly an toàn trong private subnet.

**Tài liệu đính kèm (Artifacts):**
- 🖼️ `[vpc-resource-map-20250113.png]`

---

### Bài 2.2: Máy chủ tính toán (Amazon EC2)
* **Ngày hoàn thành:** 15/01/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Khởi tạo một máy chủ Amazon EC2 (Ubuntu 24.04 LTS) sử dụng dòng `t2.micro` thuộc Free Tier.
- [x] Tạo và tải xuống an toàn cặp khóa SSH `.pem`.
- [x] Cấu hình Security Group để cho phép kết nối SSH (Port 22) từ IP tĩnh của mình và HTTP (Port 80) từ bất kỳ đâu.
- [x] Gán Elastic IP cho máy chủ để duy trì địa chỉ IPv4 public cố định khi khởi động lại.

**Khắc phục sự cố / Bài học:**
> Ban đầu gặp lỗi timeout khi cố gắng kết nối SSH. Sau khi kiểm tra, phát hiện ra Security Group đang gắn với VPC mặc định thay vì VPC tùy chỉnh mới tạo ở Bài 2.1. Đã sửa lại liên kết và SSH thành công.

---

### Bài 2.3: IAM Roles cho EC2 & AWS CLI
* **Ngày hoàn thành:** 17/01/2025
* **Thời gian thực hiện:** 2.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tạo IAM Role với quyền chỉ đọc (read-only) đối với một số dịch vụ AWS cụ thể.
- [x] Gắn trực tiếp IAM Role vào máy chủ EC2 đang chạy thông qua console.
- [x] SSH vào máy chủ và cài đặt/cấu hình AWS CLI.
- [x] Chạy các lệnh AWS CLI từ máy chủ để kiểm tra quyền truy cập mà không cần hardcode access key.

**Ghi chú & Quan sát:**
> Gắn trực tiếp IAM roles vào EC2 là một phương pháp bảo mật rất tốt. Điều này đảm bảo rằng khi triển khai các background workers hoặc logging agents — chẳng hạn như các tác vụ phục vụ cho việc phát hiện bất thường log — chúng có thể truyền dữ liệu an toàn đến các dịch vụ AWS mà không bị lộ credentials trong source code.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[ec2-trust-policy.json]`
- 💻 `[cli-output-sts-get-caller-identity.txt]`

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Xây dựng thành công hệ thống mạng tùy chỉnh an toàn và triển khai một máy chủ Linux hoạt động trơn tru bên trong đó, có thể truy cập hoàn toàn qua SSH.
* **Các khái niệm cần ôn tập lại:** Cần tìm hiểu sâu hơn về VPC Flow Logs để hiểu cách giám sát lưu lượng mạng, sẽ rất hữu ích cho việc kiểm tra và khắc phục sự cố nghẽn mạng sau này.
