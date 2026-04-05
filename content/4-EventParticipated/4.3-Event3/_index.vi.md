# 📅 Báo cáo Tổng kết: Các Sự kiện Đã tham gia

---

## Báo cáo Tổng kết: “Cloud Mastery #2 - Infrastructure as Code with Terraform”

### Mục tiêu Sự kiện
* Chia sẻ các best practices trong việc chuyển đổi từ cấu hình cloud thủ công sang tự động hóa triển khai.
* Giới thiệu các khái niệm cốt lõi của Infrastructure as Code (IaC).
* Hướng dẫn cách lựa chọn công cụ IaC (Terraform vs. CloudFormation vs. AWS CDK).
* Trình bày cách quản lý state và các lệnh Terraform cơ bản trên AWS.

### Diễn giả
* **Thịnh Nguyễn** – FCAJ Cloud Engineer Trainee

### Điểm nhấn Chính
* **Nhận diện hạn chế của phương pháp "ClickOps"**
    * Cấu hình thủ công trên giao diện console rất chậm và dễ gây ra lỗi con người.
    * Thiếu tính nhất quán giữa các môi trường (Dev, Staging, Prod).
    * Khó khăn trong việc cộng tác và không có version control (quản lý phiên bản) cho sự thay đổi hạ tầng.
* **Chuyển đổi sang Infrastructure as Code (IaC)**
    * Quản lý tài nguyên cloud thông qua các file định nghĩa có thể đọc bằng máy.
    * **Hệ sinh thái Terraform:** Hiểu về cách tiếp cận khai báo (declarative) – định nghĩa hệ thống *cần trông như thế nào* thay vì *làm sao để tạo ra nó*.
* **Cơ chế cốt lõi của Terraform**
    * Tìm hiểu sâu các lệnh: `init`, `validate`, `plan`, `apply`, và `destroy`.
    * **Quản lý State:** Cách file `terraform.tfstate` đóng vai trò là nguồn chân lý (source of truth) ánh xạ code với tài nguyên thực tế trên AWS.

### Bài học Cốt lõi
* **Tư duy Thiết kế**
    * **Ưu tiên Tự động hóa:** Hạ tầng phải được đối xử giống hệt như mã nguồn ứng dụng — được lưu trữ phiên bản, review và kiểm thử.
* **Kiến trúc Kỹ thuật**
    * **Theo dõi trạng thái (Stateful tracking):** Hiểu cách Terraform quản lý state giúp ngăn chặn sự sai lệch hạ tầng (drift) và các sửa đổi không phép.
* **Chiến lược Hiện đại hóa**
    * Chọn công cụ phù hợp với đội ngũ: Terraform cho đa nền tảng (multi-cloud), AWS CDK cho logic thiên về lập trình viên, hoặc CloudFormation cho các thiết lập thuần AWS.

### Áp dụng vào Công việc
* **Áp dụng IaC vào dự án:** Chuyển đổi việc cấu hình hạ tầng cloud của SmartHire AI từ thủ công sang các template Terraform.
* **Tích hợp CI/CD:** Tự động hóa lệnh `terraform plan` và `apply` bên trong các pipeline GitHub Actions.

### Trải nghiệm Sự kiện
Tham gia workshop **“Cloud Mastery #2”** mang lại giá trị rất lớn, giúp tôi có cái nhìn toàn diện về hiện đại hóa việc cấp phát hạ tầng. Trải nghiệm chính bao gồm:
* **Học hỏi từ diễn giả:** Thịnh Nguyễn đã chia sẻ góc nhìn thực tế về những rủi ro của "ClickOps" và cách khắc phục.
* **Tiếp cận kỹ thuật:** Học cách xem trước các thay đổi một cách an toàn với `terraform plan` và bảo mật file state.
* **Tận dụng công cụ hiện đại:** Khám phá Terraform cùng với các lựa chọn thay thế như Pulumi và OpenTofu.
* **Bài học rút ra:** Cấu hình cloud thủ công chỉ tốt cho việc học thuật; môi trường production bắt buộc phải dùng IaC để đảm bảo tính nhất quán.

### Một số hình ảnh sự kiện
*[Thêm hình ảnh sự kiện của bạn tại đây]*

**Nhìn chung, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi định hình lại tư duy về độ tin cậy của hạ tầng, sự cộng tác trong team và triển khai tự động.**

---

## Báo cáo Tổng kết: “Architecting for the Cloud with Kubernetes”

### Mục tiêu Sự kiện
* Chia sẻ best practices trong việc điều phối container và triển khai microservices.
* Giới thiệu kiến trúc và các thành phần cốt lõi của Kubernetes (K8s).
* Hướng dẫn chạy các cluster chuẩn production sử dụng Amazon EKS.
* Trình bày các công cụ thiết yếu như Helm và K9s để hỗ trợ vòng đời quản lý cluster.

### Diễn giả
* **Bảo Huỳnh** – Junior Cloud Native Developer, Endava Vietnam / Founder of ITea Lab

### Điểm nhấn Chính
* **Nhận diện hạn chế của các setup container cơ bản**
    * Docker Compose hoạt động tốt trên local nhưng gặp khó khăn với tính năng tự phục hồi, mở rộng và cân bằng tải trên production.
* **Chuyển đổi sang Điều phối Kubernetes**
    * **Kiến trúc cốt lõi:** Control Plane vs. Worker Nodes. Hiểu rõ về Pods, Deployments, và Services.
    * **Amazon EKS:** AWS quản lý Kubernetes control plane, giúp loại bỏ gánh nặng phải tự vận hành hạ tầng cluster tính sẵn sàng cao bằng tay.
* **Công cụ Hệ sinh thái Kubernetes**
    * **Helm:** Đóng vai trò là trình quản lý gói (package manager) cho K8s, cho phép team dùng chung các template có phiên bản (`values.yaml`) cho nhiều môi trường khác nhau.
    * **K9s:** Giao diện UI trên terminal giúp tương tác với cluster nhanh hơn rất nhiều khi cần check log và giám sát pod so với lệnh `kubectl` truyền thống.

### Bài học Cốt lõi
* **Tư duy Thiết kế**
    * **Resilience by design (Bền bỉ từ cốt lõi):** Hệ thống phải tự động khởi động lại các container bị lỗi và phân phối lưu lượng mượt mà.
* **Kiến trúc Kỹ thuật**
    * **Managed Kubernetes:** Việc dùng Amazon EKS hiệu quả hơn rất nhiều so với tự cài đặt cluster K8s từ đầu.
* **Chiến lược Hiện đại hóa**
    * Chuẩn hóa quy trình deploy trên Dev, Staging và Prod bằng các Helm charts.

### Áp dụng vào Công việc
* **Refactor microservices:** Đảm bảo các thành phần ứng dụng được container hóa đúng cách và phi trạng thái (stateless) để phù hợp với yêu cầu điều phối.
* **Áp dụng công cụ EKS:** Thử nghiệm dùng Helm chart để deploy các dịch vụ backend.

### Trải nghiệm Sự kiện
Workshop **“Architecting for the Cloud with Kubernetes”** mang lại kiến thức cực kỳ giá trị về cách scale ứng dụng. Trải nghiệm chính bao gồm:
* **Học hỏi từ diễn giả:** Anh Bảo cung cấp lộ trình rõ ràng từ nền tảng Docker lên kiến trúc Kubernetes cho doanh nghiệp.
* **Tiếp cận kỹ thuật:** Hiểu cách hoạt động của K8s manifests và thao tác nhanh với cluster qua K9s.
* **Bài học rút ra:** Tự quản lý hạ tầng raw rất phức tạp; tận dụng managed services như EKS và package manager như Helm giúp giảm thiểu rủi ro vận hành.

### Một số hình ảnh sự kiện
*[Thêm hình ảnh sự kiện của bạn tại đây]*

**Nhìn chung, sự kiện giúp tôi thay đổi hoàn toàn tư duy về tính sẵn sàng cao, điều phối microservices và các phương pháp vận hành cloud-native hiện đại.**

---

## Báo cáo Tổng kết: “Elixir as a Unified Solution for DevOps Infrastructure”

### Mục tiêu Sự kiện
* Chia sẻ best practices trong việc xây dựng các hệ thống backend đồng thời cao (highly concurrent) và chịu lỗi tốt.
* Giới thiệu mô hình lập trình hàm (functional programming) và máy ảo BEAM.
* Hướng dẫn cách xử lý lỗi bằng OTP và triết lý "Let It Crash".
* Trình bày các chiến lược tối ưu chi phí thực tế khi thay thế các hệ thống serverless truyền thống.

### Diễn giả
* **Nguyễn Tạ Minh Triết** – R&D Member, ITea Lab / SAP Developer Intern

### Điểm nhấn Chính
* **Nhận diện hạn chế của các mô hình đồng thời (concurrency) truyền thống**
    * Các luồng (threads) cấp hệ điều hành thường nặng và tốn kém tài nguyên.
    * Lập trình phòng thủ (defensive programming) với quá nhiều khối `try/catch` làm rác mã nguồn.
* **Chuyển đổi sang Elixir và BEAM VM**
    * **Tiến trình siêu nhẹ (Lightweight Processes):** BEAM process dùng cực ít RAM, cho phép chạy hàng triệu process đồng thời trên một máy chủ.
    * **Triết lý "Let It Crash":** Thay vì cố gắng bắt từng lỗi, các process được giám sát (supervised) sẽ cứ để cho chết, sau đó Supervisor sẽ lập tức khởi động lại chúng ở trạng thái sạch.
* **Tối ưu chi phí Thực tế (ROI)**
    * **Case Study:** Viết lại một luồng xử lý dữ liệu đang dùng AWS API Gateway + Lambda (Node.js) sang Elixir đã giảm chi phí chóng mặt. (VD: Một hệ thống lưu lượng cao tốn hơn $30,000/tháng tiền serverless đã giảm xuống còn chưa tới $400/tháng khi dùng backend Elixir).
* **Hot Code Upgrades:** Khả năng cập nhật phiên bản mới của hệ thống mà không gây ra bất kỳ thời gian chết (downtime) nào.

### Bài học Cốt lõi
* **Tư duy Thiết kế**
    * **Ưu tiên khả năng chịu lỗi:** Thiết kế hệ thống tự phục hồi ngay lập tức từ các lỗi bất ngờ thay vì cố gắng ngăn chặn mọi rủi ro thất bại.
* **Kiến trúc Kỹ thuật**
    * **Actor Model:** Phương pháp hiệu quả để cô lập trạng thái (state) và xử lý đồng thời quy mô lớn mà không cần cơ chế khóa (locking) truyền thống.
* **Chiến lược Hiện đại hóa**
    * Mặc dù Serverless (Lambda) rất tốt, nhưng với các ứng dụng có lượng kết nối đồng thời liên tục cực lớn, việc dùng ngôn ngữ hiệu suất cao như Elixir trên máy chủ cố định (EC2/Containers) mang lại ROI tốt hơn nhiều.

### Áp dụng vào Công việc
* **Đánh giá lựa chọn compute:** Đánh giá cẩn thận xem một workload phù hợp với Serverless (chạy ngắt quãng) hay máy chủ cố định (kết nối đồng thời cao) để tối ưu chi phí.
* **Áp dụng mô hình Supervisor:** Đưa các khái niệm tự phục hồi và tự động khởi động lại tương tự vào kiến trúc microservices hiện tại.

### Trải nghiệm Sự kiện
Workshop **“Elixir in DevOps”** mang lại góc nhìn vô cùng mới mẻ về lập trình hàm và độ bền bỉ của hệ thống. Trải nghiệm chính bao gồm:
* **Học hỏi từ diễn giả:** Có thêm hiểu biết về các kiến trúc thay thế, thách thức lại tiêu chuẩn "mặc định dùng serverless".
* **Tiếp cận kỹ thuật:** Hiểu cách máy ảo BEAM xử lý các tiến trình nhẹ so với Java hoặc Node.js.
* **Tận dụng công cụ hiện đại:** Khám phá khái niệm Cập nhật code nóng (Hot Code Upgrades) và cây Supervisor.
* **Bài học rút ra:** Việc lựa chọn công nghệ ảnh hưởng trực tiếp đến biên lợi nhuận (ROI) của doanh nghiệp. Chọn đúng mô hình lập trình (như Elixir cho kết nối đồng thời cao) có thể tiết kiệm hàng chục ngàn đô la.

### Một số hình ảnh sự kiện
*[Thêm hình ảnh sự kiện của bạn tại đây]*

**Nhìn chung, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi tái định hình tư duy về độ tin cậy của hệ thống, các mô hình xử lý đồng thời, và tác động tài chính của các quyết định kiến trúc.**