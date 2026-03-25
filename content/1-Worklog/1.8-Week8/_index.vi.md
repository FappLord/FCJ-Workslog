---
title: "Tuần 8: GuardScript — Phát triển tính năng, Module mã hóa & Cải thiện Frontend"
date: 2026-03-09
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### 1. Mục tiêu

* **Controller Layer:** Triển khai tất cả controllers còn lại — quản lý project, file, license, team và access control.
* **Module Crypto:** Xây dựng module mã hóa cho việc lưu trữ file đã encrypt và phân phối script an toàn qua ECDH key exchange.
* **Hệ thống Script Loader:** Phát triển các loader Python và Node.js cho end-user.
* **Cải thiện Frontend:** Sửa lỗi UI, phát triển sidebar, cập nhật logo và documentation.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Project & File Controllers** | - Triển khai `projectController.js`: CRUD, toggle active, reset stats, cài đặt project.<br>- Triển khai `fileController.js`: duyệt file tree, upload, tìm kiếm, entry point management.<br>- Sửa lỗi trang workspace — layout bị vỡ trên một số viewport.<br>- Merge PR Fix-UI, tạo README cho dự án. | Hoàn thành |
| **Ba** | **Module Crypto** | - Xây dựng `crypto.js`: AES-256-GCM encryption/decryption, X25519 ECDH key exchange, HKDF key derivation, HMAC-SHA256. | Hoàn thành |
| **Tư** | **License Controller & Sidebar** | - Triển khai `licenseController.js`: tạo license đơn/hàng loạt, HWID lock, export, hết hạn.<br>- Kiểm thử tính năng thu gọn sidebar trên nhiều kích thước màn hình. | Hoàn thành |
| **Năm** | **Script Loaders & Sidebar UI** | - Phát triển Python Loader (ECDH handshake, AES-256-GCM decryption, HWID) và Node.js Loader (multi-file manifest, VM sandbox).<br>- Sửa sidebar UI, thay đổi logo, sửa dashboard quick-action pointers. | Hoàn thành |
| **Sáu** | **Access/Team Controllers & Cleanup** | - Xây dựng `accessController.js` (IP whitelist/blacklist) và `teamController.js` (mời, role, xóa thành viên).<br>- Dọn dẹp code thừa, thêm link repo vào documentations. | Hoàn thành |

### 3. Kết quả đạt được

#### Kỹ thuật:
* **Controller Layer hoàn chỉnh:** Tất cả 10 controllers đã triển khai.
* **Pipeline mã hóa end-to-end:** File upload → gzip → AES-256-GCM → lưu trữ; ECDH handshake → session key → gửi tới client → giải mã trong sandbox.
* **Hệ thống Loader:** Cả Python và Node.js loader hoạt động với ECDH key exchange và hardware fingerprinting.
* **Quản lý License:** Vòng đời license hoàn chỉnh — tạo, HWID lock, hết hạn, xuất dữ liệu.

#### Frontend:
* Sửa lỗi trang workspace, sidebar thu gọn được, logo mới, README hoàn chỉnh.
* Merge PR#3 Fix-UI thành công, dọn dẹp import không sử dụng.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** ECDH key exchange thêm ~100ms độ trễ mỗi handshake.
* **Giải pháp:** Chấp nhận đánh đổi — bảo mật quan trọng hơn, handshake chỉ xảy ra 1 lần mỗi phiên.

### 5. Bước tiếp theo
* Bắt đầu migration sang AWS — thiết kế kiến trúc serverless.
* Tạo SAM/CloudFormation template.
* Tiếp tục cải thiện UI tổng thể.


