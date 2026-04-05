---
title: "Sự kiện 3"
date: 2026-04-04
weight: 3
chapter: false
pre: " <b> 4.3 </b> "
---

# 📅 Báo cáo Tổng kết: Các Sự kiện Đã tham gia

---

## Báo cáo Tổng kết: "Cloud Mastery #2 – Hạ tầng dưới dạng Code với Terraform"

### Mục tiêu Sự kiện
* Chia sẻ best practices trong việc chuyển đổi từ việc cấu hình cloud thủ công sang triển khai tự động.
* Giới thiệu các khái niệm cốt lõi của Hạ tầng dưới dạng Code (IaC).
* Hướng dẫn lựa chọn công cụ IaC phù hợp (Terraform vs. CloudFormation vs. AWS CDK).
* Trình bày thực hành về quản lý state của Terraform và các lệnh cơ bản trên AWS.

### Diễn giả
* **Thinh Nguyễn** – FCAJ Cloud Engineer Trainee

### Điểm nhấn Chính
* **Nhận diện hạn chế của cách làm "ClickOps"**
    * Cấu hình thủ công qua console chậm và dễ xảy ra lỗi do con người.
    * Thiếu nhất quán giữa các môi trường (Dev, Staging, Prod).
    * Khó cộng tác và thiếu kiểm soát phiên bản cho các thay đổi hạ tầng.
* **Chuyển đổi sang Hạ tầng dưới dạng Code (IaC)**
    * Quản lý tài nguyên cloud thông qua các tệp định nghĩa có thể đọc được bằng máy.
    * **Hệ sinh thái Terraform:** Hiểu cách tiếp cận khai báo (declarative) để định nghĩa *hạ tầng trông như thế nào* thay vì *cách xây dựng nó*.
* **Cơ chế Cốt lõi của Terraform**
    * Tìm hiểu sâu về các lệnh: `init`, `validate`, `plan`, `apply` và `destroy`.
    * **Quản lý State:** Cách `terraform.tfstate` đóng vai trò là nguồn sự thật, ánh xạ các cấu hình với tài nguyên AWS thực tế.

### Bài học Cốt lõi
* **Tư duy Thiết kế**
    * **Ưu tiên tự động hóa:** Hạ tầng cần được đối xử như code ứng dụng — có kiểm soát phiên bản, được review và kiểm thử.
* **Kiến trúc Kỹ thuật**
    * **Theo dõi có trạng thái (Stateful tracking):** Hiểu cách Terraform theo dõi các thay đổi giúp ngăn chặn sự trôi dạt hạ tầng (infrastructure drift) và các sửa đổi trái phép.
* **Chiến lược Hiện đại hóa**
    * **Chọn đúng công cụ cho nhóm:** Terraform cho multi-cloud, AWS CDK cho logic hướng developer, hoặc CloudFormation cho các thiết lập thuần AWS.

### Áp dụng vào Công việc
* **Chuyển đổi cấu hình thủ công sang Terraform:** Bắt đầu đưa hạ tầng hiện có vào các tệp `.tf` để kiểm soát phiên bản.
* **Triển khai state locking:** Sử dụng backend S3 + DynamoDB để quản lý `terraform.tfstate` an toàn trong môi trường nhóm.
* **Tích hợp IaC vào CI/CD pipeline:** Tự động hóa `terraform plan` và `apply` như một phần của quy trình triển khai.

### Trải nghiệm Sự kiện
Tham gia sự kiện **"Cloud Mastery #2 – Hạ tầng dưới dạng Code với Terraform"** tại Đại học FPT là một trải nghiệm vô cùng bổ ích. Những điểm nổi bật bao gồm:
* **Học hỏi từ một trainee đồng nghiệp:** Góc nhìn thực tế, trực tiếp của anh Thinh giúp kiến thức trở nên dễ hiểu và dễ áp dụng hơn nhiều.
* **Tiếp cận kỹ thuật sâu sắc:** Các buổi demo trực tiếp `terraform plan` và `apply` làm rõ toàn bộ quy trình IaC từ code đến tài nguyên cloud.
* **Kết nối và thảo luận:** Gặp gỡ các trainee cloud khác và có những cuộc trò chuyện hiệu quả về các best practices để quản lý hạ tầng ở quy mô lớn.
* **Bài học rút ra:** IaC không chỉ là về tự động hóa — đó là việc mang kỷ luật kỹ thuật phần mềm (kiểm soát phiên bản, code review, kiểm thử) vào quản lý hạ tầng.

### Một số hình ảnh sự kiện
*[Thêm hình ảnh sự kiện của bạn tại đây]*

**Nhìn chung, sự kiện củng cố quan điểm rằng việc xem hạ tầng như code là một sự thay đổi tư duy căn bản — giúp cải thiện đáng kể tính nhất quán, khả năng cộng tác và sự tự tin trong các lần triển khai cloud.**
