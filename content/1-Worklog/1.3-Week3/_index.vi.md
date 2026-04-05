---
title: "Tuần 3 - Nhật ký Công việc"
date: 2026-01-19
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

# ☁️ Nhật ký Thực tập AWS: Tuần 3 - Lưu trữ, Cơ sở dữ liệu & Auto Scaling

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 19/01/2025 - 25/01/2025  
**Mục tiêu:** Triển khai các giải pháp cơ sở dữ liệu có khả năng mở rộng, cấu hình lưu trữ object an toàn cho frontend, và thiết lập tự động mở rộng máy chủ.

Tài liệu này theo dõi tiến độ Tuần 3 trong quá trình đi OJT tại AWS của mình. Dựa trên hạ tầng mạng đã thiết lập ở tuần trước, trọng tâm của tuần này là bổ sung khả năng lưu trữ, quản lý dữ liệu bền vững và đảm bảo tính sẵn sàng cao (High Availability).

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 3.1: Lưu trữ Object (Amazon S3)
* **Ngày hoàn thành:** 20/01/2025
* **Thời gian thực hiện:** 2.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tạo Amazon S3 bucket mới với tên định danh duy nhất (globally unique).
- [x] Tắt tính năng "Block Public Access" và gắn JSON Bucket Policy tùy chỉnh để cho phép quyền đọc public đối với các file cụ thể.
- [x] Bật tính năng Static Website Hosting (Lưu trữ trang web tĩnh) trên bucket.
- [x] Tải lên file `index.html` và `error.html` mẫu để kiểm tra đường dẫn.

**Ghi chú & Quan sát:**
> S3 static hosting cực kỳ tiết kiệm chi phí. Giải pháp này hoàn toàn phù hợp để host các file tĩnh sau khi build của các ứng dụng React frontend mà không cần phải thuê các web server chuyên dụng.

**Tài liệu đính kèm (Artifacts):**
- 📄 `[s3-public-read-policy.json]`

---

### Bài 3.2: Cơ sở dữ liệu quan hệ (Amazon RDS)
* **Ngày hoàn thành:** 22/01/2025
* **Thời gian thực hiện:** 4.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Cấu hình DB Subnet Group nhắm vào các Private Subnets đã tạo ở Tuần 2.
- [x] Khởi tạo một RDS MySQL thuộc Free Tier (dòng db.t3.micro).
- [x] Cấu hình RDS Security Group để chỉ cho phép luồng truy cập vào cổng 3306 *duy nhất* từ Security Group của máy chủ ứng dụng EC2.
- [x] Kết nối thành công tới database từ máy chủ EC2 (dùng làm bastion host) thông qua MySQL CLI.

**Khắc phục sự cố / Bài học:**
> Đặt RDS trong private subnet đảm bảo nó không có Public IP, bảo vệ hoàn toàn khỏi internet. Mô hình cơ sở dữ liệu này chính xác là những gì mình cần để kết nối an toàn với các dịch vụ backend Java Spring Boot sẽ triển khai sau này.

**Tài liệu đính kèm (Artifacts):**
- 🖼️ `[rds-connectivity-success-20250122.png]`

---

### Bài 3.3: Tính Sẵn sàng Cao (Amazon EC2 Auto Scaling)
* **Ngày hoàn thành:** 24/01/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Tạo EC2 Launch Template chứa AMI và Security Groups đã cấu hình từ Tuần 2.
- [x] Khởi tạo Auto Scaling Group (ASG) trải dài trên nhiều public subnets.
- [x] Thiết lập giới hạn dung lượng Tối thiểu, Mong muốn và Tối đa (VD: Min: 1, Max: 3).
- [x] Cấu hình Target Tracking Scaling Policy để tự động thêm máy chủ nếu mức sử dụng CPU trung bình vượt quá 70%.
- [x] Thực hiện stress-test trên máy chủ chính để kích hoạt sự kiện scale-out (mở rộng).

**Ghi chú & Quan sát:**
> Việc quan sát ASG tự động tạo thêm máy chủ mới trong lúc stress-test là một minh chứng tuyệt vời cho tính linh hoạt (elasticity) của cloud. Cần đảm bảo Launch Template có chứa script khởi động (User Data) để máy chủ mới bật lên là ứng dụng đã sẵn sàng chạy.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Cách ly thành công tầng database trong mạng nội bộ mà vẫn duy trì được quyền truy cập bảo mật, đồng thời thiết lập được cơ chế mở rộng máy chủ tự động để đảm bảo tính sẵn sàng cao.
* **Các khái niệm cần ôn tập lại:** Cần thực hành tạo các policy sao chép S3 chéo tài khoản (cross-account replication), và tìm hiểu thêm về RDS Read Replicas để tối ưu khả năng mở rộng database.
