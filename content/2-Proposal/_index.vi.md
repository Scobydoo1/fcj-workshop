# 🚀 Đề xuất Dự án: SmartHire AI

**Tên dự án:** SmartHire AI  
**Loại hình:** Nền tảng Tuyển dụng & Phỏng vấn Thông minh (Cloud-Native AI)  
**Kiến trúc:** Serverless AWS / React 18 (Vite) / Terraform IaC / PostgreSQL (pgvector)  

## 1. Tóm tắt Dự án
**SmartHire AI** là một nền tảng tuyển dụng serverless có khả năng mở rộng cao, được thiết kế để loại bỏ các điểm nghẽn của quy trình tuyển dụng truyền thống. Bằng cách tận dụng kiến trúc hướng sự kiện (event-driven) của AWS, các luồng xử lý AI viết bằng Python, và kết nối GraphQL thời gian thực, SmartHire tự động hóa việc sàng lọc hồ sơ, xếp hạng ứng viên khách quan dựa trên tìm kiếm ngữ nghĩa (semantic vector search), và cung cấp một không gian phỏng vấn trực tuyến đột phá tích hợp phân tích cảm xúc, giọng nói và code trực tiếp.

## 2. Vấn đề Hiện tại
Quy trình tuyển dụng truyền thống đang gặp phải nhiều bất cập nghiêm trọng:
- **Mất quá nhiều thời gian lọc hồ sơ:** Nhân sự phải đọc thủ công các CV không theo cấu trúc chuẩn, dẫn đến thời gian xử lý chậm và gây nghẽn quy trình.
- **Đánh giá chủ quan & Phụ thuộc từ khóa:** Các hệ thống ATS thông thường chỉ tìm kiếm từ khóa chính xác (keyword matching), bỏ lỡ những ứng viên giỏi nhưng sử dụng từ ngữ khác trong CV.
- **Phỏng vấn online thiếu chiều sâu:** Các cuộc gọi video thông thường không cung cấp được dữ liệu về hành vi, khiến nhà tuyển dụng khó đánh giá sự tự tin, kỹ năng giao tiếp hay sự bình tĩnh của ứng viên.
- **Quy trình phân mảnh:** Nhà tuyển dụng phải dùng quá nhiều công cụ rời rạc để đăng tin, theo dõi ứng viên, làm bài test code, và ghi hình phỏng vấn.

## 3. Giải pháp Đề xuất & Tính năng Chính

### 🎯 1. Cổng Ứng viên (Candidate Portal) Mượt mà
- **Xác thực Bảo mật:** Đăng nhập không cần mật khẩu (passwordless) hoặc qua mạng xã hội được hỗ trợ bởi Amazon Cognito, quản lý state toàn cục qua `authStore`.
- **Tải file trực tiếp lên Cloud:** Sử dụng AWS S3 Pre-signed URLs (`CVUploadWidget.tsx`), cho phép ứng viên tải các file PDF nặng trực tiếp lên S3, hoàn toàn bỏ qua giới hạn dung lượng của API Gateway và không làm nghẽn backend.
- **Gợi ý việc làm Động:** Ứng viên xem các công việc phù hợp do AI gợi ý trên dashboard, kèm theo thang điểm độ phù hợp trực quan (`MatchScoreGauge`).

### 📊 2. Dashboard Nhà tuyển dụng & Xử lý AI Thời gian thực
- **Tự động Phân tích & Điều phối:** Khi một CV được tải lên, sự kiện từ S3 sẽ kích hoạt AWS Step Function (`state_machine_cv_processing.asl.json`). Máy trạng thái này điều phối các Lambda Python (`cv_parser.py` và `jd_parser.py`) để trích xuất kỹ năng, học vấn và kinh nghiệm.
- **Ghép nối Ngữ nghĩa (Semantic Vector Matching):** Hồ sơ ứng viên và Mô tả công việc (JD) được chuyển đổi thành vector (embeddings) và lưu trong Amazon RDS PostgreSQL sử dụng extension `pgvector`. Điều này giúp hệ thống ghép nối dựa trên ý nghĩa ngữ cảnh, không chỉ dựa vào từ khóa chính xác.
- **Cập nhật AppSync Real-time:** Ngay khi engine AI (`candidate_ranking_engine`) tính điểm xong, AWS AppSync sẽ đẩy dữ liệu qua GraphQL subscriptions xuống frontend (`useAppSyncSubscription.ts`), tự động cập nhật bảng Xếp hạng Ứng viên mà không cần F5 tải lại trang.

### 🎙️ 3. Không gian Phỏng vấn Thông minh (Interview Workspace)
Phòng họp trực tuyến tích hợp WebRTC được thiết kế riêng cho đánh giá kỹ thuật và hành vi:
- **Đánh giá Hành vi:** Các React hooks tùy chỉnh chạy trực tiếp trên trình duyệt để phân tích ứng viên. `useEmotionAnalysis.ts` theo dõi biểu cảm khuôn mặt, trong khi `useMicVolume.ts` giám sát sự tự tin trong giọng nói và những khoảng ngập ngừng.
- **Trình chạy Code trực tiếp:** Môi trường thực thi code tích hợp (`useCodeRunner.ts`) cho phép nhà tuyển dụng làm bài test kỹ thuật trực tiếp mà không cần dùng nền tảng của bên thứ 3.
- **Đánh giá STAR Tự động:** Giọng nói được chuyển thành văn bản theo thời gian thực (`useSpeechTranscript.ts`) và gửi tới `star_evaluator_lambda.py`, nơi AI sẽ chấm điểm câu trả lời dựa trên mô hình STAR (Tình huống, Nhiệm vụ, Hành động, Kết quả). Báo cáo cuối cùng được tạo bởi `report_generator_lambda.py`.

## 4. Kiến trúc Kỹ thuật & DevOps
SmartHire AI được xây dựng theo tiêu chuẩn bảo mật doanh nghiệp và khả năng mở rộng tối đa:
- **Tầng Frontend:** React (TypeScript), Vite, Tailwind CSS, UI components của shadcn/ui, và hỗ trợ Theme (Dark/Light mode). Lưu trữ trên Amazon S3 và phân phối toàn cầu qua Amazon CloudFront.
- **Tầng API & Dữ liệu:** Amazon API Gateway (REST), AWS AppSync (GraphQL), và Amazon RDS (PostgreSQL).
- **Tầng Tính toán & Điều phối:** Hoàn toàn Serverless sử dụng AWS Step Functions, Amazon SQS/SNS để xử lý hàng đợi (decoupled), và AWS Lambda cho toàn bộ logic AI và backend.
- **Cơ sở hạ tầng dạng Code (IaC):** Toàn bộ môi trường AWS được module hóa (Networking, Auth, Database, Processing, Storage) và triển khai tự động bằng **Terraform**.
- **Pipeline CI/CD:** Tự động hóa hoàn toàn qua GitHub Actions (`deploy.yml`). Các thay đổi code trên nhánh `main` sẽ kích hoạt quy trình build, đồng bộ an toàn lên S3 và xóa cache CloudFront thông qua xác thực OIDC.

## 5. Kết quả Mong đợi & Giá trị Doanh nghiệp
- **Giảm 70% Thời gian Tuyển dụng:** Việc sàng lọc tự động giúp nhà tuyển dụng dành toàn bộ thời gian để tập trung vào nhóm ứng viên xuất sắc nhất.
- **Phát hiện Nhân tài Ẩn giấu:** Tìm kiếm ngữ nghĩa (`pgvector`) đảm bảo các ứng viên giỏi không bị loại chỉ vì CV của họ thiếu một vài "buzzword" cụ thể.
- **Tuyển dụng Dựa trên Dữ liệu:** Không gian phỏng vấn thông minh loại bỏ cảm tính của con người bằng cách cung cấp các chỉ số đo lường khách quan về kỹ năng giao tiếp, trình độ kỹ thuật và sự ổn định tâm lý của ứng viên.
