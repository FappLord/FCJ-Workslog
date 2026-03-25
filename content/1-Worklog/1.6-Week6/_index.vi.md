---
title: "Tuần 6: Hội nhập sau Tết & Thiết kế dự án GuardScript"
date: 2026-02-23
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### 1. Mục tiêu

* **Đồng bộ nhóm:** Kết nối lại với Team TheBois sau kỳ nghỉ Tết; rà soát tiến độ và thống nhất hướng dự án.
* **Chốt dự án:** Chính thức chọn **GuardScript** làm dự án chính cho kỳ thực tập FCJ và xác định phạm vi.
* **Thiết kế kiến trúc:** Thiết kế kiến trúc hệ thống tổng thể, database schema và cấu trúc API.
* **Nghiên cứu:** Tìm hiểu các kỹ thuật mã hóa (AES-GCM, ECDH) và chiến lược bảo vệ mã nguồn liên quan đến dự án.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Đồng bộ nhóm** | - Kết nối lại với Team TheBois sau 2 tuần nghỉ Tết.<br>- Rà soát các ý tưởng dự án từ Tuần 5.<br>- Chính thức chọn **GuardScript** làm dự án chính. | Hoàn thành |
| **Ba** | **Xác định phạm vi** | - Định nghĩa tính năng cốt lõi:<br>&nbsp;+ Quản lý dự án theo workspace<br>&nbsp;+ Phân phối script được mã hóa (Python, Node.js)<br>&nbsp;+ Quản lý license key với khóa phần cứng (HWID)<br>&nbsp;+ Cộng tác nhóm theo vai trò<br>&nbsp;+ Kiểm soát truy cập (IP whitelist/blacklist) | Hoàn thành |
| **Tư** | **Thiết kế kiến trúc** | - Thiết kế backend: Express.js + SQLite cho bản prototype ban đầu.<br>- Lên kế hoạch modular controller pattern (auth, project, file, license, workspace, team, access).<br>- Phác thảo cấu trúc API route (~70 endpoints). | Hoàn thành |
| **Năm** | **Nghiên cứu Crypto** | - Nghiên cứu AES-256-GCM cho mã hóa nội dung file.<br>- Tìm hiểu ECDH (X25519) key exchange cho handshake loader an toàn.<br>- Đánh giá PBKDF2 (210K iterations) cho password hashing so với bcrypt. | Hoàn thành |
| **Sáu** | **Thiết lập phát triển** | - Khởi tạo project Node.js với Express framework.<br>- Thiết lập cấu trúc repository dự án.<br>- Tạo `package.json` với dependencies ban đầu.<br>- Cấu hình môi trường phát triển và công cụ. | Hoàn thành |

### 3. Kết quả đạt được

#### Kỹ thuật:
* **Kế hoạch kiến trúc:** Thiết kế modular monolith backend với phân tách rõ ràng:
    * **Controllers:** 10 controller chuyên biệt theo domain, xử lý các khía cạnh khác nhau.
    * **Utils:** Các module tái sử dụng: crypto, auth, rate-limiting, response.
    * **Storage:** Lưu trữ file dựa trên filesystem với mã hóa at-rest.
* **Thiết kế bảo mật:** Chọn các phương pháp mã hóa tiêu chuẩn công nghiệp:
    * AES-256-GCM cho mã hóa nội dung file.
    * ECDH key exchange cho handshake loader.
    * PBKDF2-SHA256 (210K iterations) cho lưu mật khẩu.
    * JWT (HMAC-SHA256) cho token xác thực.

#### Dự án (Team TheBois):
* **Phạm vi đã chốt:** Team đồng ý scope GuardScript — tập trung vào vấn đề cốt lõi là chống tái phân phối code trái phép.
* **Kiến trúc đồng bộ:** Tất cả thành viên hiểu kiến trúc hệ thống đã lên kế hoạch.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** Chọn giữa SQLite (đơn giản, file-based) vs PostgreSQL (mạnh mẽ, networked) cho prototype.
* **Giải pháp:** Chọn SQLite cho giai đoạn prototype nhờ zero-config và tính portable. Lên kế hoạch migrate sang DynamoDB cho giai đoạn triển khai AWS.

### 5. Bài học rút ra
* Xác định scope dự án rõ ràng từ sớm giúp tránh feature creep.
* Modular controller pattern giúp dễ dàng phân chia công việc giữa các thành viên.
* Chọn đúng cryptographic primitives ngay từ đầu rất quan trọng cho ứng dụng yêu cầu bảo mật cao.

### 6. Bước tiếp theo
* Bắt đầu phát triển GuardScript backend.
* Triển khai database schema và module xác thực.
* Xây dựng controller layer cho workspace và project management.


