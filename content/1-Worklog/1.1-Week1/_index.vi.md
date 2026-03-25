---
title: "Tuần 1: Giới thiệu & Thiết lập môi trường làm việc"
date: 2026-01-05
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### 1. Mục tiêu

* **Hòa nhập:** Kết nối với các thành viên FCJ, nắm bắt văn hóa và quy định.
* **Kỹ thuật:** Thiết lập môi trường AWS (Account, CLI) và hoàn thành chuỗi bài thực hành cơ bản (Explore AWS).
* **Quản lý (Team Lead):** Thiết lập hạ tầng làm việc và phân chia vai trò cho team **TheBois**.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Onboarding** | - Làm quen với các thành viên FCJ.<br>- Đọc và nghiên cứu nội quy, quy trình làm việc tại đơn vị thực tập. | Hoàn thành |
| **Ba** | **AWS Overview** | - Tìm hiểu kiến thức nền tảng về các nhóm dịch vụ:<br>&nbsp;+ Compute (EC2, Lambda)<br>&nbsp;+ Storage (S3, EBS)<br>&nbsp;+ Database (RDS, DynamoDB)<br>&nbsp;+ Networking (VPC) | Hoàn thành |
| **Tư** | **Setup Environment** | - Tạo tài khoản AWS Free Tier.<br>- Cài đặt và cấu hình **AWS CLI** trên máy local.<br>- Kết nối terminal với tài khoản AWS qua Access Key/Secret Key. | Hoàn thành |
| **Năm** | **Explore AWS Labs** | - Thực hành hoàn thành **5/5 activities** trong mục Explore AWS để nhận Credits:<br>&nbsp;1. Tạo Database (Aurora/RDS)<br>&nbsp;2. Tạo Web App với AWS Lambda<br>&nbsp;3. Setup ngân sách với AWS Budgets<br>&nbsp;4. Sử dụng Foundation Model trên **Amazon Bedrock**<br>&nbsp;5. Khởi tạo EC2 Instance cơ bản | Hoàn thành |
| **Sáu** | **Team Management** | - **Setup Communication:** Tạo server Discord, thiết lập các channel thảo luận.<br>- **Setup Source Control:** Khởi tạo GitHub Organization/Repo cho team TheBois.<br>- **Role Division:** Họp team, phân chia vai trò cụ thể (AI, IA, Cyber, Backend) cho từng thành viên. | Hoàn thành |

### 3. Kết quả đạt được

#### Kỹ thuật:
* **Môi trường:** Đã cấu hình xong AWS CLI, đảm bảo việc tương tác với AWS thông suốt từ máy cá nhân.
* **Thực hành:** Hoàn thành xuất sắc **100% (5/5)** các bài lab khởi động của AWS:
    * Đã trải nghiệm deploy mô hình AI trên **Amazon Bedrock**.
    * Đã deploy thành công serverless app với **Lambda**.
    * Đã khởi tạo database và máy ảo EC2.
    * Đã thiết lập cảnh báo chi phí (Budget) để quản lý tài nguyên.

#### Quản lý (Team TheBois):
* **Hạ tầng làm việc:** Đã có không gian làm việc chung trên Discord.
    * Đã có GitHub Repo để quản lý source code dự án sắp tới.
* **Nhân sự:** Các thành viên (Bình, Trí, Hiển, Tùng, Vinh) đã nắm rõ role và nhiệm vụ của mình.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** Việc setup IAM User ban đầu gặp chút khó khăn về quyền hạn.
* **Giải pháp:** Đã đọc tài liệu AWS IAM Best Practices và cấu hình lại Policy phù hợp.
