---
title: "Tuần 7: GuardScript — Phát triển Backend cốt lõi & Khởi động Frontend"
date: 2026-03-02
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### 1. Mục tiêu

* **Nền tảng Backend:** Khởi tạo backend GuardScript với Express.js và triển khai database schema bằng SQLite.
* **Hệ thống xác thực:** Xây dựng module auth hoàn chỉnh với JWT tokens và PBKDF2 password hashing.
* **Các module cốt lõi:** Triển khai quản lý workspace và các thao tác CRUD cơ bản cho project.
* **Khởi động Frontend:** Bắt đầu xây dựng giao diện web song song với backend.
* **Bắt đầu phát triển:** Dự án GuardScript chính thức bắt đầu ngày **06/03/2026**.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Rà soát kiến trúc** | - Chốt kiến trúc backend với team.<br>- Rà soát controller-service-util pattern.<br>- Phân công: bản thân phụ trách frontend, các thành viên phụ trách backend và infrastructure. | Hoàn thành |
| **Ba** | **Thiết lập Express.js** | - Khởi tạo ứng dụng Express.js với middleware stack (CORS, JSON body parsing, cookie handling).<br>- Thiết lập cấu trúc route cho 70+ API endpoints trên 10 controllers. | Hoàn thành |
| **Tư** | **Database Schema** | - Thiết kế và triển khai SQLite schema: Users, Workspaces, Projects, Licenses, Access Lists, Logs, Team Members tables. | Hoàn thành |
| **Năm** | **Module Auth & Frontend** | - Triển khai module auth: PBKDF2-SHA256 password hashing, JWT token, timing-safe comparison.<br>- Xây dựng `authController.js` và `workspaceController.js`.<br>- Bắt đầu xây dựng giao diện landing page và các trang auth. | Hoàn thành |
| **Sáu** | **Cải thiện UI & Dọn dẹp** | - Cải thiện giao diện tổng thể — chỉnh sửa spacing, colors, responsive.<br>- Cấu hình `.gitignore`, dọn dẹp file dữ liệu không cần thiết trong repo. | Hoàn thành |

### 3. Kết quả đạt được

#### Kỹ thuật:
* **Backend Server:** Express.js server hoạt động với routing có cấu trúc cho tất cả API endpoints.
* **Database Layer:** SQLite schema hoàn chỉnh với 10+ tables, foreign key và indexed columns.
* **Hệ thống Auth:** PBKDF2 với 210K iterations, JWT tokens với TTL 7 ngày.
* **Rate Limiting:** Giới hạn tốc độ theo IP và scope.

#### Frontend:
* Bắt đầu xây dựng landing page, trang login/register.
* Thiết lập cấu trúc thư mục frontend và CSS design tokens.

#### Chất lượng Code:
* Phân tách rõ ràng — controllers xử lý HTTP, utils xử lý business logic, database xử lý persistence.
* Bảo mật ưu tiên: không lưu mật khẩu plaintext, so sánh timing-safe.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** Thiết kế hệ thống workspace linh hoạt hỗ trợ cả cá nhân và nhóm.
* **Giải pháp:** Triển khai RBAC với 4 cấp: `owner > admin > editor > viewer`.

### 5. Bước tiếp theo
* Triển khai các controller còn lại: project, file, license, team, access.
* Xây dựng module mã hóa và hệ thống script loader.
* Tiếp tục phát triển frontend dashboard và workspace.


