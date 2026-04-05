---
title: "Nhật ký công việc"
date: 2026-04-04
weight: 1
chapter: false
pre: "<b>1. </b>"
---

# 🚀 Tổng kết Hành trình 10 tuần Kỹ thuật AWS & SmartHire

**Trạng thái:** 🟢 Đã hoàn thành  
**Thời gian:** Tháng 1/2025 - Tháng 3/2025  
**Dự án:** SmartHire AI & Hạ tầng AWS Cloud  

Tài liệu này cung cấp cái nhìn tổng quan về hành trình 10 tuần thực tập thực tế (OJT) của mình. Khóa đào tạo được chia thành hai giai đoạn chính: thiết lập hạ tầng cloud nền tảng và phát triển nền tảng tuyển dụng tích hợp AI (cloud-native).

---

## 🏗️ Giai đoạn 1: Nền tảng Cốt lõi AWS (Tuần 1–5)
Nửa đầu của kỳ thực tập tập trung vào việc thiết lập một hạ tầng cloud bảo mật, bền bỉ và có khả năng mở rộng để phục vụ các ứng dụng doanh nghiệp.

* **Tuần 1 (Bảo mật & Quản trị):** Khóa tài khoản root, thiết lập cảnh báo ngân sách (zero-spend), và triển khai các chính sách quản lý định danh (IAM) nghiêm ngặt kèm MFA dành cho quản trị viên hàng ngày.
* **Tuần 2 (Mạng & Máy chủ):** Thiết kế kiến trúc mạng nội bộ (VPC) tùy chỉnh với public/private subnets và khởi tạo các máy chủ EC2 Ubuntu đầu tiên, truy cập an toàn qua SSH và gắn IAM roles.
* **Tuần 3 (Lưu trữ, CSDL & Mở rộng):** Thiết lập S3 để lưu trữ web tĩnh, cách ly cơ sở dữ liệu MySQL trong mạng nội bộ bằng RDS, và cấu hình Auto Scaling Group (ASG) để tự động xử lý tải trọng lớn.
* **Tuần 4 (Giám sát & Định tuyến):** Giám sát toàn hệ thống bằng các dashboard và cảnh báo CloudWatch tùy chỉnh, đồng thời cấu hình Route 53 để định tuyến lưu lượng DNS lai (hybrid DNS).
* **Tuần 5 (Dự án Kiến trúc tổng hợp):** Kết hợp tất cả các thành phần nền tảng để triển khai một ứng dụng web 3 lớp (3-tier) có tính sẵn sàng cao và khả năng chịu lỗi, sử dụng Application Load Balancers (ALB) và cơ chế tự động chuyển dự phòng (Multi-AZ) cho database.

---

## 💻 Giai đoạn 2: Phát triển Hệ thống SmartHire AI (Tuần 6–10)
Nửa sau của lộ trình chuyển hướng hoàn toàn sang phát triển ứng dụng (front-end), xây dựng cổng thông tin SmartHire AI bằng React/Vite và tích hợp sâu với các dịch vụ cloud-native của AWS.

* **Tuần 6 (Khởi động dự án & Xác thực):** Dựng khung source code React và thiết lập luồng xác thực bảo mật phân quyền (Ứng viên & Nhà tuyển dụng) bằng Amazon Cognito, phân phối an toàn qua CloudFront.
* **Tuần 7 (Cổng Ứng viên & Upload S3):** Xây dựng dashboard cho ứng viên với giao diện hiện đại (shadcn) và thiết kế cơ chế tải CV cực kỳ tối ưu, đẩy file trực tiếp lên S3 qua Pre-signed URLs nhằm tránh làm nghẽn backend.
* **Tuần 8 (Cổng Nhà tuyển dụng & Dữ liệu Real-time):** Phát triển giao diện quản lý tuyển dụng và tích hợp AWS AppSync (GraphQL) để truyền trực tiếp điểm số đánh giá AI của ứng viên xuống front-end theo thời gian thực qua WebSockets.
* **Tuần 9 (Không gian Phỏng vấn trực tuyến):** Xử lý các state phức tạp cho phòng phỏng vấn trực tiếp, tích hợp WebRTC, theo dõi âm lượng mic và các hook phân tích cảm xúc.
* **Tuần 10 (CI/CD & Hoàn thiện):** Chuốt lại trải nghiệm người dùng với tính năng Quản lý Theme toàn cục (Dark Mode) và tự động hóa quy trình triển khai bằng việc xây dựng pipeline CI/CD với GitHub Actions, tự động đồng bộ code lên S3 và xóa cache CloudFront một cách bảo mật qua OIDC.

---
*Kết thúc Nhật ký Thực tập OJT 10 Tuần*
