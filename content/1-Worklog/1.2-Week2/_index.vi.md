---
title: "Tuần 2: Lưu trữ, Cơ sở dữ liệu & Khởi động Dự án"
date: 2026-01-12
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### 1. Mục tiêu tuần 2

* **Kỹ thuật cốt lõi:** Tìm hiểu sâu về các dịch vụ Lưu trữ (S3, EBS) và Cơ sở dữ liệu (RDS) của AWS; thực hành xây dựng hệ thống upload file.
* **Khởi động dự án:** Hoàn thiện đề xuất cho dự án **"Website Security Baseline Assessment Platform"** – công cụ hỗ trợ đánh giá nhanh rủi ro bảo mật.
* **Nâng cao kỹ năng:** Củng cố kiến thức NLP thông qua các chứng chỉ Coursera để phục vụ cho khía cạnh AI của dự án thực tập.

### 2. Chi tiết công việc trong tuần (Weekly Tasks Breakdown)

| Thứ | Công việc chính | Chi tiết | Trạng thái | Link / Minh chứng |
|:---:|:---|:---|:---:|:---|
| **Hai** | **Lưu trữ & CSDL** | - Nghiên cứu **S3** (Buckets, lifecycle policies).<br>- Nghiên cứu **EBS** (Volumes, snapshots) & **RDS** (Cài đặt, quản lý).<br>- *Nguồn: Chương trình học Tuần 2*. | Hoàn thành | [\] |
| **Ba** | **Thực hành Lab** | - **Xây dựng hệ thống upload file:**<br>&nbsp;+ Cấu hình S3 bucket để lưu trữ.<br>&nbsp;+ Kết nối backend với S3 để xử lý file. | Hoàn thành | [\] |
| **Tư** | **Đề xuất dự án** | - **Soạn thảo Proposal:** Xác định phạm vi cho "Website Security Baseline Assessment Platform".<br>- **Chốt tính năng:**<br>&nbsp;+ Kiểm tra cơ bản: HTTPS/SSL, Robots.txt.<br>&nbsp;+ Quét lỗ hổng: SQL Injection, XSS, File Uploads.<br>- **Kiến trúc:** Thiết kế core độc lập (chạy Local/VPS/AWS) không phụ thuộc cứng vào hạ tầng cloud. | Hoàn thành | [Link tới File Proposal](https://docs.google.com/document/d/1oSdWCVFiCKTUP9ol8eZyOwYg9J5DhtE1/edit?usp=sharing&ouid=101583017547639870148&rtpof=true&sd=true) |
| **Năm** | **Chứng chỉ AI/NLP** | - Hoàn thành 2 khóa học DeepLearning.AI trên Coursera:<br>&nbsp;1. NLP with Attention Models.<br>&nbsp;2. NLP with Classification and Vector Spaces. | Hoàn thành | [Link tới Cert 1](https://www.coursera.org/account/accomplishments/verify/177J1KWEAWPH)<br>[Link tới Cert 2](https://www.coursera.org/account/accomplishments/verify/JCCLTKPCI1CV) |
| **Sáu** | **AWS Specialization** | - Tìm kiếm và lên kế hoạch học "AWS Fundamentals Specialization".<br>- Review tuần và họp nhóm rút kinh nghiệm. | Đang thực hiện | [Link tới khóa AWS Fundamentals Specialization](https://www.coursera.org/programs/fptu-spring-2026-6010y/specializations/aws-fundamentals?source=search) |

### 3. Kết quả chính (Key Results)

#### Kỹ thuật & Thực hành:
* **Thành thạo Lưu trữ:** Đã hiểu và quản lý được S3 Lifecycles và EBS Snapshots.
* **Triển khai thực tế:** Xây dựng thành công **Hệ thống Upload File** sử dụng AWS S3, đảm bảo dữ liệu được lưu trữ bền vững.

#### Dự án (Team TheBois):
* **Hoàn thiện Proposal:** Đã xong đề xuất cho **Website Security Baseline Assessment Platform**.
* **Xác định phạm vi:** Thống nhất tập trung vào "Đánh giá nền tảng" (tiền kiểm thử/pre-pentest) để nhận diện rủi ro phổ biến như Injection, Phân quyền (Access Control), và Cấu hình sai (Security Misconfiguration).
* **Chiến lược kiến trúc:** Quyết định kiến trúc linh hoạt: AWS dùng để lưu trữ báo cáo/log, nhưng core logic quét lỗi hoạt động độc lập (Portable).

#### Chứng chỉ & Học tập:
* **Hoàn thành Coursera:** Đạt 2 chứng chỉ từ DeepLearning.AI (hoàn thành ngày 15/01/2026):
    * *Natural Language Processing with Attention Models*
    * *Natural Language Processing with Classification and Vector Spaces*

### 4. Vấn đề & Giải pháp (Issues & Solutions)
* **Vấn đề:** Khó khăn trong việc xác định phạm vi pháp lý khi quét các website bên ngoài.
* **Giải pháp:** Đã làm rõ trong proposal - Tuân thủ nguyên tắc "Chỉ thực hiện khi có sự đồng ý bằng văn bản".