---
title: "Sự kiện: AWS re:Invent Recap"
date: 2026-01-27
weight: 1
chapter: false
pre: " <b> 1.4.1. </b> "
---

# Báo cáo tổng hợp: “AWS re:Invent 2025 Recap (Vietnam)”

### Thông tin sự kiện
| | |
|:---|:---|
| **Thời gian** | 27 Tháng 1, 2026 |
| **Địa điểm** | Văn phòng AWS Vietnam (Tầng 26 & 36), TP. Hồ Chí Minh |
| **Vai trò** | Người tham dự (FCJ Cloud Intern) |

### Mục tiêu tham dự

- Cập nhật những công bố quan trọng nhất từ hội nghị AWS re:Invent 2025 (Las Vegas).
- Tìm hiểu sâu về Generative AI, đặc biệt là Agentic AI (AI tác vụ) và Amazon Bedrock.
- Khám phá các tối ưu hóa mới về dữ liệu và hạ tầng (SageMaker, S3).
- Giao lưu, kết nối với các AWS Solution Architects và cộng đồng công nghệ.

### Diễn giả

- **Anh Thi** – Solution Architect (Chủ đề: Generative AI & Agents)
- **Anh Tùng** – Diễn giả (Chủ đề: OpenSearch & Agentic Search)
- **Các Solution Architect & Account Manager khác từ AWS**

### Nội dung nổi bật (Key Highlights)

#### Phiên 1: Generative AI & Agents

- **Mô hình Amazon Nova:** Giới thiệu các mô hình nền tảng hiệu suất cao mới.
- **Bedrock Agents:** Đi sâu vào Orchestration (Điều phối), Flows, và các tính năng mới như **Memory (Bộ nhớ)** và **Guardrails (Vành đai bảo vệ)**.
- **Agentic AI:** Sự chuyển dịch từ chatbot đơn giản sang các "Agent" tự chủ có khả năng thực thi quy trình nhiều bước.

#### Phiên 2: SageMaker Unified Studio & Cập nhật S3

- **Unified Studio:** Một IDE duy nhất kết nối Data Engineers, Data Scientists và AI Engineers, xóa bỏ rào cản giữa các team.
- **S3 Tables:** Hỗ trợ định dạng bảng Apache Iceberg ngay trên S3.
- **S3 Vector:** Tính năng mới cho phép lưu trữ vector trực tiếp trên S3, giúp giảm chi phí đáng kể so với việc dùng vector database chuyên dụng.

#### Phiên 3 & 4: Tìm kiếm & Đa phương thức (Multimodal)

- **OpenSearch Serverless:** Tích hợp với giao thức MCP và Agentic Memory.
- **Nova Multimodal Embeddings:** Chuyển đổi video và hình ảnh thành vector để tìm kiếm.
- **Bedrock Data Automation:** Tự động trích xuất thông tin từ dữ liệu đa phương tiện.

#### Phiên 5: Hạ tầng AI

- **SageMaker HyperPod:** Quản lý cụm GPU quy mô lớn.
- **SageMaker MLflow:** Quản lý toàn bộ vòng đời dự án Machine Learning.

### Bài học rút ra (Key Takeaways)

#### Tương lai là Agentic AI

- **Quy trình tự chủ:** Xu hướng đang chuyển từ "Prompt Engineering" sang "Agent Engineering". Các Agent có bộ nhớ có thể duy trì ngữ cảnh theo thời gian và thực hiện nhiệm vụ phức tạp mà không cần con người can thiệp liên tục.
- **Bảo mật là then chốt:** Khi Agent trở nên tự chủ, việc thiết lập Guardrails (chính sách an toàn) là bắt buộc.

#### Tối ưu hóa Dữ liệu & Tính toán

- **Hiệu quả chi phí:** **S3 Vector** là giải pháp đột phá cho các dự án cần tìm kiếm vector (như RAG) nhưng ngân sách hạn chế.
- **Hợp tác:** **SageMaker Unified Studio** giúp quy trình chuẩn bị dữ liệu và huấn luyện mô hình diễn ra liền mạch trong một môi trường.

### Ứng dụng vào công việc

- **Tích hợp vào Dự án (Security Platform):**
    - Đánh giá **Bedrock Agents** để tự động hóa quy trình "quét lỗ hổng" (ví dụ: agent chạy scan, phân tích log và tự soạn báo cáo).
    - Triển khai **S3 Vector** để lưu trữ log và các mẫu nhận diện lỗ hổng (signatures) một cách hiệu quả cho backend.
- **Tinh chỉnh Kiến trúc:** Cân nhắc sử dụng **Cognito** để quản lý người dùng thay vì tự xây dựng module auth.
- **Best Practices:** Áp dụng tư duy "Serverless first" học được từ sự kiện để giữ cho hạ tầng dự án tinh gọn.

### Trải nghiệm sự kiện

Tham dự **“AWS re:Invent 2025 Recap”** tại **Văn phòng AWS Vietnam** là một điểm nhấn quan trọng trong kỳ thực tập, giúp tôi kết nối kiến thức đám mây cơ bản với các xu hướng AI tiên tiến nhất.

#### Mở rộng tầm nhìn
- Các phiên chia sẻ đã làm rõ rằng **Agentic AI** là tương lai gần. Việc xem demo Flow Agent phân tích dữ liệu bán hàng đã khơi dậy ý tưởng cho tính năng báo cáo trong dự án của team.
- Hiểu về **Multimodal RAG** giúp tôi thấy được khả năng mở rộng không chỉ xử lý văn bản mà còn cả hình ảnh/video – điều cần thiết cho các giai đoạn sau của Security Platform (ví dụ: phân tích ảnh chụp màn hình web).

#### Kiểm chứng giải pháp kỹ thuật
- Việc ra mắt **S3 Vector** đã xác nhận nhu cầu của team về một giải pháp lưu trữ tiết kiệm chi phí. Đây là câu trả lời trực tiếp cho vấn đề chi phí lưu trữ log mà chúng tôi đang gặp phải.
- Trao đổi với anh Thi và các SA khác giúp tôi giải tỏa các thắc mắc về **IAM Policies** và các mô hình **Serverless** mà tôi đã gặp khó khăn trong Tuần 3.

#### Kết nối cộng đồng
- Không khí tại văn phòng AWS (Tầng 26 & 36) rất sôi động, với nhiều builders và developers cùng chia sẻ các bài toán thực tế.
- Tôi đã có cơ hội thảo luận về dự án của team **"TheBois"** với các chuyên gia trong ngành và nhận được những phản hồi giá trị về kiến trúc đề xuất.

> Nhìn chung, sự kiện không chỉ cập nhật kiến thức kỹ thuật mà còn cung cấp các công cụ cụ thể (Agents, S3 Vector) mà tôi có thể áp dụng ngay vào dự án **Website Security Baseline Assessment Platform**.