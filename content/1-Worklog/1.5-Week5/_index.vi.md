# ☁️ Nhật ký Thực tập AWS: Tuần 5 - Dự án cuối khóa: Ứng dụng Web tính sẵn sàng cao

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** 02/02/2025 - 08/02/2025  
**Mục tiêu:** Tích hợp các dịch vụ AWS cốt lõi để thiết kế và triển khai một ứng dụng web 3 lớp (3-tier) bền bỉ và có tính sẵn sàng cao.

Tài liệu này theo dõi tiến độ Tuần 5. Tuần này là đỉnh cao của chuỗi đào tạo nền tảng, thực hiện "Workshop Ứng dụng Web Tính sẵn sàng cao". Mục tiêu là kết hợp mạng, máy chủ, lưu trữ và cơ sở dữ liệu thành một hệ thống thống nhất, có khả năng chịu lỗi.

---

## 📅 Nhật ký Công việc Hàng ngày

### Bài 5.1: Thiết kế Kiến trúc & Chuẩn bị Mạng
* **Ngày hoàn thành:** 03/02/2025
* **Thời gian thực hiện:** 2.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Phân tích bản thiết kế kiến trúc 3 lớp (3-tier) được cung cấp trong workshop.
- [x] Kiểm tra lại VPC đã tạo ở Tuần 2 để đảm bảo các public subnet đã sẵn sàng cho Load Balancer và private subnet được cách ly hoàn toàn cho Application Server và Database.
- [x] Cấu hình ma trận Security Group tập trung (ALB -> EC2 -> RDS) để kiểm soát luồng truy cập nghiêm ngặt.

**Ghi chú & Quan sát:**
> Việc thiết kế các ranh giới mạng trước giúp quá trình triển khai trơn tru hơn rất nhiều. Mô hình 3 lớp này chính là chuẩn mực mà mình sẽ dùng để triển khai các ứng dụng thực tế: frontend React (Lớp 1/Edge), API Java Spring Boot (Lớp 2/Compute), và cơ sở dữ liệu MySQL (Lớp 3/Data).

---

### Bài 5.2: Triển khai Tầng Dữ liệu (Multi-AZ RDS)
* **Ngày hoàn thành:** 05/02/2025
* **Thời gian thực hiện:** 3.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Nâng cấp RDS instance đơn lẻ từ Tuần 3 lên mô hình Multi-AZ (Đa vùng sẵn sàng).
- [x] Xác minh bản sao dự phòng (standby replica) ở Availability Zone thứ hai.
- [x] Thực hiện khởi động lại thủ công kèm tính năng chuyển đổi dự phòng (failover) để kiểm tra độ bền của database và theo dõi thời gian gián đoạn (downtime).

**Khắc phục sự cố / Bài học:**
> Quá trình failover mất vài phút, trong thời gian đó endpoint của database tạm thời không phản hồi trước khi DNS cập nhật trỏ về bản sao dự phòng. Logic thử lại (retry logic) ở tầng ứng dụng Spring Boot sẽ rất quan trọng để xử lý mượt mà các gián đoạn ngắn này.

---

### Bài 5.3: Tầng Máy chủ & Application Load Balancer
* **Ngày hoàn thành:** 06/02/2025
* **Thời gian thực hiện:** 4.5 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Khởi tạo Application Load Balancer (ALB) nằm trên hai public subnets.
- [x] Cập nhật Auto Scaling Group (ASG) từ Tuần 3 để tự động đăng ký các máy chủ mới vào ALB Target Group.
- [x] Triển khai một backend API mẫu lên các EC2 thông qua script khởi động User Data.
- [x] Cấu hình Health Checks (Kiểm tra sức khỏe) trên ALB để đảm bảo traffic chỉ được điều hướng đến các máy chủ đang hoạt động tốt.

**Tài liệu đính kèm (Artifacts):**
- 🖼️ `[alb-target-group-healthy.png]`
- 📄 `[ec2-bootstrap-userdata.sh]`

---

### Bài 5.4: Tích hợp Frontend & Kiểm thử toàn hệ thống
* **Ngày hoàn thành:** 08/02/2025
* **Thời gian thực hiện:** 3.0 giờ
* **Trạng thái:** [ ] Chưa làm | [ ] Đang làm | [x] Đã xong

**Công việc đã thực hiện:**
- [x] Lưu trữ các file của ứng dụng frontend trên S3 bucket đã cấu hình ở Tuần 3.
- [x] Cập nhật cấu hình API của frontend để trỏ đến DNS name của ALB vừa tạo.
- [x] Sử dụng Route 53 để trỏ một custom domain (tên miền tùy chỉnh) về ALB.
- [x] Thực hiện stress-test toàn hệ thống bằng công cụ giả lập tải để quan sát ASG tự động mở rộng và ALB phân phối lưu lượng đồng đều.

**Ghi chú & Quan sát:**
> Việc chứng kiến toàn bộ hệ thống hoạt động đồng bộ mang lại cảm giác rất tuyệt vời. Khi CPU tăng vọt trong lúc stress-test, CloudWatch đã kích hoạt báo động, ASG tạo thêm máy chủ mới, và ALB lập tức chuyển hướng traffic tới máy chủ đó ngay khi nó vượt qua bài kiểm tra Health Check.

---

## 📝 Tổng kết Cuối Tuần
* **Thành quả lớn nhất tuần này:** Triển khai thành công kiến trúc 3 lớp hoạt động đầy đủ, có tính sẵn sàng cao, khả năng tự phục hồi và tự động mở rộng.
* **Các khái niệm cần ôn tập lại:** Cần nghiên cứu việc tích hợp AWS Certificate Manager (ACM) để kích hoạt HTTPS trên Application Load Balancer nhằm bảo mật mã hóa đường truyền (end-to-end encryption).
