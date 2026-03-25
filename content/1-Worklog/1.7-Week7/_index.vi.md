---
title: "Tuần 7: GuardScript — Phát triển Backend cốt lõi"
date: 2026-03-02
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### 1. Mục tiêu

* **Nền tảng Backend:** Khởi tạo backend GuardScript với Express.js và triển khai database schema bằng SQLite.
* **Hệ thống xác thực:** Xây dựng module auth hoàn chỉnh với JWT tokens và PBKDF2 password hashing.
* **Các module cốt lõi:** Triển khai quản lý workspace và các thao tác CRUD cơ bản cho project.
* **Bắt đầu phát triển:** Dự án GuardScript chính thức bắt đầu ngày **06/03/2026**.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Rà soát kiến trúc** | - Chốt kiến trúc backend với team.<br>- Rà soát controller-service-util pattern.<br>- Chuẩn bị môi trường phát triển cho prototyping nhanh. | Hoàn thành |
| **Ba** | **Thiết lập Express.js** | - Khởi tạo ứng dụng Express.js với middleware stack.<br>- Cấu hình CORS, JSON body parsing, cookie handling.<br>- Thiết lập cấu trúc route cho 70+ API endpoints trên 10 controllers. | Hoàn thành |
| **Tư** | **Database Schema** | - Thiết kế và triển khai SQLite schema bao gồm:<br>&nbsp;+ Users table (id, email, password hash, status, timestamps)<br>&nbsp;+ Workspaces table (id, name, owner, loader key, encryption key, settings)<br>&nbsp;+ Projects table (id, workspace, name, secret key, entry point, settings)<br>&nbsp;+ Project Files, Licenses, Access Lists, Logs, Team Members tables. | Hoàn thành |
| **Năm** | **Module Auth** | - Triển khai `src/utils/auth.js`:<br>&nbsp;+ PBKDF2-SHA256 password hashing (210.000 iterations, 16-byte salt)<br>&nbsp;+ Tạo và xác thực JWT token bằng HMAC-SHA256<br>&nbsp;+ Trích xuất token từ Authorization header và cookies<br>&nbsp;+ So sánh timing-safe để chống timing attacks. | Hoàn thành |
| **Sáu** | **Workspace & User Controllers** | - Xây dựng `authController.js`: đăng ký, đăng nhập, hồ sơ, đổi mật khẩu, xóa tài khoản.<br>- Xây dựng `workspaceController.js`: tạo, liệt kê, cập nhật, xóa workspace; bảo vệ PIN; logs. | Hoàn thành |

### 3. Kết quả đạt được

#### Kỹ thuật:
* **Backend Server:** Express.js server hoạt động đầy đủ với routing có cấu trúc cho tất cả API endpoints.
* **Database Layer:** SQLite schema hoàn chỉnh với 10+ tables, foreign key và indexed columns.
* **Hệ thống Auth:** Xác thực đạt chất lượng production:
    * PBKDF2 với 210K iterations.
    * Phát hiện SHA-256 hash cũ với đường nâng cấp tự động.
    * JWT tokens với TTL 7 ngày và vô hiệu hóa khi đổi mật khẩu.
* **Rate Limiting:** Giới hạn tốc độ theo IP và scope qua `src/utils/rateLimit.js`.

#### Chất lượng Code:
* **Cấu trúc module:** Phân tách rõ ràng — controllers xử lý HTTP, utils xử lý business logic, database xử lý persistence.
* **Bảo mật ưu tiên:** Không lưu mật khẩu plaintext, so sánh timing-safe, quản lý token đúng chuẩn.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** Thiết kế hệ thống workspace linh hoạt hỗ trợ cả sử dụng cá nhân và nhóm với các mức quyền khác nhau.
* **Giải pháp:** Triển khai hệ thống kiểm soát truy cập theo vai trò với 4 cấp: `owner > admin > editor > viewer`, kiểm tra quyền chi tiết theo từng thao tác.

### 5. Bài học rút ra
* Bắt đầu với database schema rõ ràng giúp tiết kiệm thời gian refactoring sau này.
* Số iteration PBKDF2 cần cân bằng giữa bảo mật và trải nghiệm — 210K iterations thêm ~200ms mỗi lần login, chấp nhận được.
* Tổ chức route theo domain (auth, workspace, project...) scale tốt hơn so với tổ chức theo HTTP method.

### 6. Bước tiếp theo
* Triển khai các controller còn lại: project, file, license, team, access.
* Xây dựng module mã hóa cho việc mã hóa file và phân phối script an toàn.
* Phát triển hệ thống script loader.


