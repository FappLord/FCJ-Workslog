---
title: "Tuần 4: Định danh, Bảo mật & Cập nhật re:Invent"
date: 2026-01-26
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### 1. Mục tiêu (Objectives)

* **Bảo mật & Định danh:** Làm chủ dịch vụ AWS Identity and Access Management (IAM) để bảo vệ môi trường làm việc của nhóm. Tập trung vào phân quyền chi tiết (Policies), Roles và thực thi xác thực đa yếu tố (MFA).
* **Cập nhật công nghệ:** Cập nhật các cải tiến mới nhất từ sự kiện **AWS re:Invent 2025** (Sự kiện Recap tại VN ngày 27/01).
* **Tích hợp dự án:** Đánh giá các tính năng mới (S3 Vector, Bedrock Agents) để xem xét khả năng tích hợp vào dự án **Website Security Baseline Assessment Platform**.

### 2. Chi tiết công việc trong tuần (Weekly Tasks Breakdown)

| Thứ | Công việc chính | Chi tiết | Trạng thái | Minh chứng |
|:---:|:---|:---|:---:|:---|
| **Hai** | **Kiến thức cốt lõi IAM** | - **Users & Groups:** Tạo các IAM User riêng biệt cho từng thành viên team TheBois (Binh, Tri, Hien, Tung, Vinh).<br>- **Groups:** Tổ chức User vào các nhóm chức năng (Dev, Admin, Audit) để quản lý quyền hạn hiệu quả. | Hoàn thành | \ |
| **Ba** | **Sự kiện AWS** | - **Tham dự:** Sự kiện "AWS re:Invent 2025 Recap" (27/01/2026).<br>- **Tóm tắt:** Cập nhật về GenAI (Bedrock Agents), SageMaker Unified Studio và tối ưu hóa S3.<br>*(Xem báo cáo chi tiết sự kiện ở mục riêng)* | Hoàn thành | \ |
| **Tư** | **Policies & Bảo mật** | - **Phân quyền:** Viết các JSON Policies (theo nguyên tắc Quyền tối thiểu - Least Privilege) để giới hạn quyền truy cập vào các S3 bucket và EC2 instance cụ thể.<br>- **Tăng cường bảo mật:** Bắt buộc kích hoạt **MFA (Xác thực đa yếu tố)** cho tài khoản Root và tất cả IAM User. | Hoàn thành | \ |
| **Năm** | **Đánh giá Kỹ thuật** | - Phân tích **S3 Vector** và **S3 Tables** để lưu trữ và truy xuất log tối ưu chi phí cho dự án Security Platform.<br>- Nghiên cứu khả năng của **Bedrock Agents** trong việc tự động hóa quy trình quét bảo mật. | Hoàn thành | \ |
| **Sáu** | **Chứng chỉ AWS** | - Tiếp tục học khóa **AWS Fundamentals Specialization** (Coursera).<br>- Ôn tập và so sánh các phương pháp bảo mật đã học ở Tuần 3 (VPC) so với Tuần 4 (IAM). | Đang thực hiện | \ |

### 3. Kết quả đạt được (Key Results)

#### Kỹ thuật & Thực hành:
* **Hạ tầng IAM:** Đã cấu hình hoàn chỉnh môi trường truy cập bảo mật.
    * **Users/Groups:** Đã tạo và phân nhóm xong.
    * **Policies:** Áp dụng các Policy tùy chỉnh để đảm bảo Developer chỉ truy cập được các tài nguyên liên quan đến dự án "Website Security Baseline Assessment Platform".
    * **MFA:** Triển khai thành công 100% cho toàn bộ team.
* **Tư thế bảo mật (Security Posture):** Loại bỏ hoàn toàn việc sử dụng tài khoản Root cho các tác vụ hàng ngày.

#### Cập nhật kiến thức (Tóm tắt sự kiện):
* **GenAI & Dữ liệu:** Nắm được cái nhìn tổng quan về Bedrock Agents và S3 Vector từ sự kiện AWS re:Invent Recap.
* **Ứng dụng:** Nhận thấy tiềm năng sử dụng **Cognito** (quản lý user) và **S3 Vector** (lưu trữ vector log) cho backend của dự án.
* *(Ghi chú: Nội dung chi tiết về các phiên chia sẻ và diễn giả được lưu trong tài liệu riêng.)*

### 4. Vấn đề & Giải pháp (Issues & Solutions)
* **Vấn đề:** Gặp khó khăn và phức tạp khi tự viết các JSON Policy tùy chỉnh để giới hạn tài nguyên (định dạng ARN).
* **Giải pháp:** Sử dụng công cụ **AWS Policy Generator** để tạo bản nháp, sau đó tinh chỉnh thủ công đoạn mã JSON để khớp với tên S3 bucket cụ thể của dự án.