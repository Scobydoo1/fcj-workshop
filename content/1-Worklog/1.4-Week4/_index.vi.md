---
title: "Tuần 4 - Nhật ký Công việc"
date: 2026-01-26
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

# ☁️ Nhật ký Thực tập AWS: Tuần 4 - Giám sát, DNS & Công cụ Phát triển

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 26/01/2025 - 01/02/2025  
**Mục tiêu:** Triển khai khả năng giám sát hệ thống, cấu hình định tuyến DNS lai (hybrid) và làm quen với các môi trường phát triển tích hợp trên cloud.

Tài liệu này theo dõi tiến độ Tuần 4 trong quá trình đi OJT tại AWS. Khi lưu trữ, máy chủ và cơ sở dữ liệu đã sẵn sàng, tuần này tập trung vào việc tạo ra cái nhìn toàn cảnh (visibility) về các tài nguyên đó, định tuyến lưu lượng an toàn và tối ưu hóa quy trình phát triển.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 4.1: Giám sát Hệ thống (Amazon CloudWatch)
* **Ngày hoàn thành:** 27/01/2025
* **Thời gian thực hiện:** 3.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Cài đặt CloudWatch Agent lên các máy chủ EC2 hiện có để theo dõi RAM và ổ cứng.
- [x] Tạo một CloudWatch Dashboard tùy chỉnh tập trung hiển thị CPU của EC2, số lượng kết nối RDS và lưu lượng mạng của ASG.
- [x] Thiết lập CloudWatch Alarms để tự động gửi email thông báo qua SNS nếu CPU của database vượt 80% trong 5 phút.
- [x] Khám phá CloudWatch Logs và các log group.

**Ghi chú & Quan sát:**
> Việc làm quen với CloudWatch Logs là một ưu tiên. Hiểu cách các luồng log (log streams) được thu thập và phân tích là bước đầu tiên cực kỳ cần thiết để xây dựng hệ thống phát hiện bất thường log AWS Sentinel vào cuối tháng này.

**Tài liệu đính kèm (Artifacts):**
- 🖼️ `[cloudwatch-custom-dashboard.png]`
- 📄 `[cloudwatch-agent-config.json]`

---

### Bài 4.2: DNS & Định tuyến lưu lượng (Amazon Route 53)
* **Ngày hoàn thành:** 29/01/2025
* **Thời gian thực hiện:** 3.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Đăng ký một tên miền thử nghiệm (hoặc dùng file host local để mô phỏng).
- [x] Tạo một Hosted Zone trên Route 53.
- [x] Cấu hình các bản ghi 'A' (A Records) để trỏ domain về EC2 Auto Scaling Group.
- [x] Cấu hình bản ghi Alias để trỏ trực tiếp một subdomain về S3 bucket đang chứa trang web tĩnh đã tạo ở Tuần 3.
- [x] Thiết lập hệ thống DNS lai (hybrid DNS) giữa môi trường Local mô phỏng và Amazon VPC.

**Khắc phục sự cố / Bài học:**
> Việc trỏ domain thẳng vào S3 bucket là một cách rất gọn gàng để public giao diện React frontend cho người dùng. Trong môi trường thực tế (production), mình sẽ đặt CloudFront phía trước S3 và trỏ Route 53 về CloudFront để tận dụng bộ nhớ đệm tại biên (edge caching) và hỗ trợ HTTPS.

---

### Bài 4.3: Cloud IDE & Máy chủ đơn giản (Cloud9 & Lightsail)
* **Ngày hoàn thành:** 31/01/2025
* **Thời gian thực hiện:** 2.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Khởi tạo môi trường AWS Cloud9 sử dụng máy chủ EC2 `t2.micro`.
- [x] Clone một repository mẫu vào Cloud9 IDE và thử nghiệm chỉnh sửa code trên trình duyệt cùng với việc truy cập terminal.
- [x] Triển khai một stack LAMP cấu hình sẵn trên Amazon Lightsail để so sánh sự đơn giản của nó với việc tự tạo EC2.
- [x] Phân tích sự khác biệt về chi phí giữa mức giá cố định của Lightsail và giá on-demand của EC2.

**Ghi chú & Quan sát:**
> Cloud9 cực kỳ hữu ích để sửa lỗi nhanh hoặc debug nhóm trực tiếp trên môi trường AWS. Mặc dù mình vẫn sẽ dùng EC2/EKS để triển khai ứng dụng Java Spring Boot chính, nhưng Lightsail lại là một giải pháp thay thế tuyệt vời để dựng nhanh các bản prototype.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Nắm bắt được toàn bộ trạng thái hệ thống thông qua các dashboard CloudWatch tùy chỉnh và cấu hình thành công định tuyến DNS tới cả máy chủ và bộ nhớ tĩnh.
* **Các khái niệm cần ôn tập lại:** Cần nghiên cứu thêm về Route 53 Health Checks và các chính sách định tuyến dự phòng (failover routing) để đảm bảo ứng dụng web không bị gián đoạn khi có sự cố.
