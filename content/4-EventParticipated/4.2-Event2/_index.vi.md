---
title: "Sự kiện 2"
date: 2026-03-14
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

# 📅 Báo cáo Tổng kết: Các Sự kiện Đã tham gia

---

## Báo cáo Tổng kết: "AIoT Project: Locker Management"

### Mục tiêu Sự kiện
* Chia sẻ các best practices trong việc tự động hóa quy trình vật lý thủ công bằng công nghệ cloud.
* Giới thiệu kiến trúc Edge-to-Cloud sử dụng Arduino và Raspberry Pi.
* Hướng dẫn cách kết nối thiết bị IoT với AWS một cách bảo mật.
* Trình bày các công cụ AI (AWS Rekognition) hỗ trợ xác thực danh tính vật lý.

### Diễn giả
* **Aiden Dinh** – Operation Engineer, Katalon

### Điểm nhấn Chính
* **Nhận diện hạn chế của quản lý thủ công**
    * Quy trình theo dõi vật lý thường dư thừa và tốn thời gian.
    * Vận hành kém hiệu quả → Quản lý có thể không có mặt mỗi khi thành viên muốn mượn đồ.
* **Chuyển đổi sang kiến trúc AIoT tự động**
    * **Tích hợp phần cứng:** Sử dụng Raspberry Pi làm Main Controller/MQTT Broker, và Arduino làm thiết bị biên (Edge Device) thu thập dữ liệu từ cảm biến từ (Reed Switch), thẻ RFID và Camera.
    * **AWS IoT Core:** Bảo mật kết nối và truyền dữ liệu. Định tuyến các sự kiện cảm biến tới Lambda, DynamoDB và S3 mà không cần phụ thuộc hoàn toàn vào MQTT server nội bộ.
* **Tích hợp Xác thực Khuôn mặt**
    * **AWS Rekognition:** Thực hiện nhận diện khuôn mặt để xác định thành viên nào đang truy cập tủ đồ. So sánh hình ảnh với tập dữ liệu khuôn mặt đã huấn luyện và trả về điểm số độ tin cậy để liên kết với giao dịch quét thẻ RFID.

### Bài học Cốt lõi
* **Tư duy Thiết kế (Design Mindset)**
    * **Ưu tiên tự động hóa:** Luôn tìm cách loại bỏ sự dư thừa thủ công trong các luồng công việc vật lý.
* **Kiến trúc Kỹ thuật (Technical Architecture)**
    * **Edge-to-Cloud:** Phương pháp thực tế dùng Raspberry Pi làm cầu nối giữa cảm biến local và hạ tầng AWS mở rộng.
    * Sử dụng **AWS IoT Core** thay vì MQTT server độc lập để định tuyến sự kiện bảo mật, linh hoạt.
* **Chiến lược Hiện đại hóa**
    * **Kết hợp AI và phần cứng:** Kết hợp cảm biến (RFID) với AI (Rekognition) để tạo ra hệ thống xác thực đa yếu tố an toàn.

### Áp dụng vào Công việc
* **Áp dụng kiến trúc IoT vào dự án:** Sử dụng AWS IoT Core để thu thập dữ liệu an toàn từ các thiết bị biên.
* **Triển khai AI validation:** Thử nghiệm AWS Rekognition cho các quy trình yêu cầu xác minh danh tính.

### Trải nghiệm Sự kiện
Việc tham gia workshop **"AIoT Project: Locker Management"** mang lại giá trị rất lớn, giúp tôi có cái nhìn toàn diện về việc tích hợp phần cứng với các dịch vụ AI trên cloud của AWS. Trải nghiệm chính bao gồm:
* **Học hỏi từ diễn giả kinh nghiệm:** Anh Aiden đã chia sẻ những phương pháp thực tiễn nhất để xây dựng hệ thống IoT tự động.
* **Tiếp cận kỹ thuật thực tế:** Học cách định tuyến sự kiện từ Raspberry Pi lên AWS Lambda và DynamoDB. Hiểu rõ sự đánh đổi giữa việc dùng MQTT nội bộ và AWS IoT Core.
* **Tận dụng công cụ hiện đại:** Khám phá AWS Rekognition để xác thực khuôn mặt và liên kết hành động vật lý (quét RFID) với danh tính kỹ thuật số.
* **Bài học rút ra:** Áp dụng kiến trúc AIoT giúp cải thiện bảo mật hệ thống và giảm thiểu gánh nặng vận hành thủ công.

### Một số hình ảnh sự kiện
*[Thêm hình ảnh sự kiện của bạn tại đây]*

**Nhìn chung, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi định hình lại tư duy về tích hợp hệ thống vật lý - kỹ thuật số và điện toán biên (edge computing) trên AWS.**

---

## Báo cáo Tổng kết: "Building AI Agent with Strands"

### Mục tiêu Sự kiện
* Chia sẻ các best practices trong thiết kế ứng dụng Generative AI hiện đại.
* Giới thiệu quá trình chuyển đổi từ các mô hình LLM đơn thuần sang các AI Agent tự chủ.
* Hướng dẫn cách chọn và tích hợp công cụ (API, database).
* Trình bày framework Strands để hỗ trợ vòng đời phát triển Agent.

### Diễn giả
* **Bành Cẩm Vinh**

### Điểm nhấn Chính
* **Nhận diện hạn chế của LLM đơn thuần**
    * Không thể lấy dữ liệu thời gian thực → Dẫn đến "ảo giác" (hallucinations) và câu trả lời lỗi thời.
    * Thiếu khả năng thực thi → Không thể thay mặt người dùng thực hiện hành động.
* **Chuyển đổi sang kiến trúc Agentic**
    * **Suy luận đa bước (Multi-step reasoning):** Agent có thể tự động lên kế hoạch và thực thi các workflow phức tạp.
    * **Tích hợp công cụ:** Cho phép LLM truy cập API, database và dịch vụ bên ngoài.
    * **Vòng lặp tác vụ (Agentic Loop / Tool Calling):** Quá trình AI tự quyết định công cụ cần dùng, chờ kết quả và lập kế hoạch cho bước tiếp theo.
* **System Prompts & Cơ sở Tri thức**
    * Định nghĩa hành vi tự chủ nghiêm ngặt và tích hợp kiến thức chuyên ngành để phản hồi linh hoạt theo ngữ cảnh.

### Bài học Cốt lõi
* **Tư duy Thiết kế**
    * **Định hướng hành động:** Tiến xa hơn các giao diện chatbot tĩnh để xây dựng các Agent có khả năng ra quyết định.
* **Kiến trúc Kỹ thuật**
    * **Tool Calling:** Phương pháp thiết yếu để mô hình hóa các workflow nơi AI cần giao tiếp với hệ thống bên ngoài.
* **Chiến lược Hiện đại hóa**
    * Áp dụng các framework như Strands để chuẩn hóa cách tích hợp công cụ và system prompt vào ứng dụng LLM.

### Áp dụng vào Công việc
* **Áp dụng Agentic workflow vào dự án:** Nâng cấp các giao diện chat thông thường thành các agent tự chủ có khả năng gọi các hàm backend.
* **Triển khai tool calling:** Kết nối các cơ sở dữ liệu và API của dự án hiện tại với LLM.

### Trải nghiệm Sự kiện
Tham gia workshop **"Building AI Agent with Strands"** là một trải nghiệm cực kỳ giá trị, giúp tôi hiểu rõ về việc hiện đại hóa các ứng dụng AI. Trải nghiệm chính bao gồm:
* **Học hỏi từ diễn giả:** Có được cái nhìn sâu sắc về suy luận đa bước và hành vi tự chủ của AI.
* **Tiếp cận kỹ thuật:** Học cách xây dựng Agentic Loop và định nghĩa công cụ trong framework Strands.
* **Bài học rút ra:** Việc chỉ dựa vào LLM sẽ giới hạn năng lực của ứng dụng; tích hợp công cụ giúp lấy dữ liệu thời gian thực và tạo ra các phản hồi mang tính động.

### Một số hình ảnh sự kiện
*[Thêm hình ảnh sự kiện của bạn tại đây]*

**Nhìn chung, sự kiện giúp tôi thay đổi hoàn toàn tư duy về thiết kế ứng dụng AI và các luồng công việc tự chủ.**

---

## Báo cáo Tổng kết: "Automated Prompt Engineering: Enhancing LLM Output Quality"

### Mục tiêu Sự kiện
* Chia sẻ best practices về prompt engineering và "nghệ thuật giao tiếp với AI".
* Giới thiệu các thành phần có cấu trúc của prompt để loại bỏ các chỉ thị mơ hồ.
* Hướng dẫn xây dựng kiến trúc serverless tự động để tối ưu hóa prompt.
* Trình bày các dịch vụ AWS (Bedrock, CloudWatch) hỗ trợ GenAIOps và giám sát hệ thống.

### Diễn giả
* **Nguyễn Tuấn Thịnh** – DevOps Engineer, First Cloud AI Journey

### Điểm nhấn Chính
* **Nhận diện hậu quả của việc giao tiếp kém với AI**
    * Prompt chung chung → Đầu ra chung chung, không sử dụng được.
    * Chỉ thị mơ hồ → Kết quả thiếu nhất quán giữa các lần chạy.
    * Lãng phí token → Tăng chi phí API và giảm hiệu suất.
* **Chuyển đổi sang Prompt có cấu trúc**
    * **Thành phần cốt lõi:** Vai trò (Role), Chỉ thị (Instruction), Ngữ cảnh (Context), Dữ liệu đầu vào, Định dạng đầu ra, Ví dụ, và Ràng buộc/Nguyên tắc.
* **Kiến trúc GenAIOps Serverless**
    * **Amazon Bedrock:** Làm engine LLM lõi mà không cần tự huấn luyện mô hình.
    * **Amazon DynamoDB:** Cơ sở dữ liệu NoSQL lưu trữ dữ liệu người dùng, prompt và lịch sử tối ưu với độ trễ tính bằng mili-giây.
    * **Amazon CloudWatch:** Thu thập log và theo dõi các chỉ số hiệu suất (độ trễ API, tỷ lệ lỗi) để giám sát sức khỏe hệ thống theo thời gian thực.

### Bài học Cốt lõi
* **Tư duy Thiết kế**
    * **Ưu tiên cấu trúc:** Luôn thiết lập prompt một cách có hệ thống thay vì xem nó như một cuộc trò chuyện thông thường.
* **Kiến trúc Kỹ thuật**
    * **GenAIOps:** Phương pháp thực tế để mô hình hóa và giám sát các luồng Generative AI trên môi trường production.
    * Sử dụng **CloudWatch metrics** để quan sát độ trễ API và lượng token tiêu thụ.
* **Chiến lược Hiện đại hóa**
    * Triển khai **Amazon Bedrock** để sử dụng các mô hình nền tảng dạng managed service thay vì tự host các mô hình nặng nề trên EC2.

### Áp dụng vào Công việc
* **Áp dụng prompt có cấu trúc vào dự án:** Refactor lại toàn bộ prompt trong ứng dụng để đảm bảo có đủ 7 thành phần cốt lõi (Role, Context, Constraints...).
* **Áp dụng GenAIOps:** Dùng thử Amazon CloudWatch để giám sát độ trễ và tỷ lệ lỗi của Bedrock API trong môi trường hiện tại.

### Trải nghiệm Sự kiện
Workshop **"Automated Prompt Engineering"** mang lại góc nhìn cực kỳ giá trị về việc tối ưu hóa LLM thông qua các phương pháp và công cụ tiên tiến. Trải nghiệm chính bao gồm:
* **Học hỏi từ diễn giả:** Góc nhìn của một kỹ sư DevOps về GenAI đã làm nổi bật tầm quan trọng của việc tối ưu chi phí và quản lý token.
* **Tiếp cận kỹ thuật:** Học cách sử dụng DynamoDB để lưu trữ lịch sử prompt và CloudWatch để giám sát "sức khỏe" của hệ thống AI.
* **Bài học rút ra:** Những prompt được kỹ sư hóa tốt sẽ giảm lãng phí token đồng thời cải thiện độ tin cậy của đầu ra. Giám sát ứng dụng AI cũng quan trọng không kém gì việc giám sát các microservices truyền thống.

### Một số hình ảnh sự kiện
*[Thêm hình ảnh sự kiện của bạn tại đây]*

**Nhìn chung, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi tái định hình tư duy về prompt engineering, khả năng quan sát hệ thống (observability) và tối ưu hóa chi phí trong kỷ nguyên GenAI.**
