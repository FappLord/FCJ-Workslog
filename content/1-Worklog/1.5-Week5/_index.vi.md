---
title: "Tuần 5: Tìm hiểu Serverless & Hình thành ý tưởng dự án"
date: 2026-02-02
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### 1. Mục tiêu

* **Nắm vững Serverless:** Tìm hiểu chuyên sâu về AWS Lambda, API Gateway và DynamoDB — các thành phần cốt lõi của kiến trúc serverless.
* **Tiến độ chứng chỉ:** Tiếp tục khóa AWS Fundamentals Specialization trên Coursera.
* **Ý tưởng dự án:** Brainstorm và đánh giá các ý tưởng dự án với Team TheBois cho project thực tập FCJ.
* **Tổng kết trước Tết:** Hệ thống lại kiến thức Tuần 1–4 trước kỳ nghỉ Tết Nguyên đán.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Lambda Deep Dive** | - Nghiên cứu mô hình thực thi Lambda, cold start và pricing.<br>- Tìm hiểu Lambda Function URL như endpoint API gọn nhẹ.<br>- Thực hành tạo Lambda function với Node.js runtime. | Hoàn thành |
| **Ba** | **API Gateway & DynamoDB** | - So sánh API Gateway REST vs HTTP API.<br>- Nghiên cứu sâu DynamoDB: partition key, sort key, GSI, query patterns.<br>- Tìm hiểu chế độ PAY_PER_REQUEST của DynamoDB. | Hoàn thành |
| **Tư** | **Thực hành Lab** | - Xây dựng serverless REST API đơn giản:<br>&nbsp;+ Lambda function xử lý CRUD.<br>&nbsp;+ DynamoDB table lưu dữ liệu.<br>&nbsp;+ Test qua Lambda Function URL. | Hoàn thành |
| **Năm** | **Brainstorm Dự án** | - Họp Team TheBois thảo luận hướng dự án.<br>- Đánh giá các ý tưởng: phân phối mã nguồn an toàn, quản lý license, cloud-based code editor.<br>- Hình thành ý tưởng ban đầu cho **GuardScript** — nền tảng phân phối và bảo vệ mã nguồn với hệ thống licensing. | Hoàn thành |
| **Sáu** | **Tổng kết trước Tết** | - Hệ thống lại ghi chú từ Tuần 1–5.<br>- Tiếp tục AWS Fundamentals Specialization (Coursera).<br>- Chuẩn bị task backlog cho sau Tết.<br>- *Lưu ý: Tuần sau bắt đầu nghỉ Tết (2 tuần).* | Hoàn thành |

### 3. Kết quả đạt được

#### Kỹ thuật:
* **Kiến thức Serverless:** Hiểu rõ thực tiễn bộ ba Lambda + API Gateway + DynamoDB, tạo nền tảng cho việc triển khai GuardScript lên AWS sau này.
* **Thực hành:** Xây dựng và test thành công serverless CRUD API, xác minh tính khả thi của kiến trúc backend dựa trên Lambda.

#### Dự án (Team TheBois):
* **Xác định ý tưởng:** Hình thành ý tưởng cốt lõi cho **GuardScript** — nền tảng phân phối mã nguồn bảo mật, giải quyết vấn đề tái phân phối code trái phép.
* **Danh sách tính năng ban đầu:** Phân phối script được mã hóa, quản lý license, khóa phần cứng (HWID), cách ly theo workspace, kiểm soát truy cập.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** DynamoDB yêu cầu thiết kế partition key và GSI cẩn thận ngay từ đầu, không linh hoạt như SQL.
* **Giải pháp:** Nghiên cứu Single-Table Design vs Multi-Table Design. Quyết định dùng multi-table với GSI có mục tiêu rõ ràng cho GuardScript.

### 5. Bài học rút ra
* Kiến trúc serverless đòi hỏi tư duy khác so với thiết kế server truyền thống — statelessness, cold start và pricing pay-per-use đều ảnh hưởng đến quyết định kiến trúc.
* Thiết kế schema DynamoDB phải hướng theo query, không phải hướng theo entity.

### 6. Bước tiếp theo
* Nghỉ Tết Nguyên đán (2 tuần).
* Quay lại với scope dự án GuardScript đã được chốt.
* Bắt đầu thiết kế kiến trúc và lập kế hoạch phát triển.


