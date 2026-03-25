---
title: "Tuần 8: GuardScript — Phát triển tính năng & Module mã hóa"
date: 2026-03-09
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### 1. Mục tiêu

* **Controller Layer:** Triển khai tất cả controllers còn lại — quản lý project, file, license, team và access control.
* **Module Crypto:** Xây dựng xương sống mã hóa cho việc lưu trữ file đã encrypt và phân phối script an toàn qua ECDH key exchange.
* **Hệ thống Script Loader:** Phát triển các loader Python và Node.js phân phối code đã mã hóa cho end-user.
* **Kiểm soát truy cập:** Triển khai IP whitelist/blacklist và khóa phần cứng (HWID) cho quản lý license.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Project & File Controllers** | - Triển khai `projectController.js`: CRUD, toggle active, reset stats, cài đặt project (yêu cầu license, khóa HWID, IP whitelist, rate limits).<br>- Triển khai `fileController.js`: duyệt cây file, chỉnh sửa nội dung, upload, tìm kiếm (plaintext & regex), sao chép, rename, di chuyển, quản lý entry point. | Hoàn thành |
| **Ba** | **Module Crypto** | - Xây dựng `src/utils/crypto.js`:<br>&nbsp;+ Mã hóa/giải mã AES-256-GCM cho nội dung file.<br>&nbsp;+ Tạo cặp khóa X25519 ECDH và dẫn xuất shared secret.<br>&nbsp;+ HKDF key derivation, SHA-256 hashing, Base64-URL encoding.<br>&nbsp;+ HMAC-SHA256 cho kiểm tra tính toàn vẹn. | Hoàn thành |
| **Tư** | **License Controller** | - Triển khai `licenseController.js`:<br>&nbsp;+ Tạo license đơn và hàng loạt với custom keys.<br>&nbsp;+ Xuất license, bật/tắt trạng thái.<br>&nbsp;+ Bật/tắt khóa HWID và reset HWID.<br>&nbsp;+ Hỗ trợ ngày hết hạn. | Hoàn thành |
| **Năm** | **Script Loaders** | - Phát triển **Python Loader** (`python/unified-loader.py`):<br>&nbsp;+ ECDH handshake với server để trao đổi khóa.<br>&nbsp;+ Giải mã script AES-256-GCM phía client.<br>&nbsp;+ Tạo Hardware ID (MAC, hostname, CPU, OS).<br>- Phát triển **Node.js Loader** (`javascript_nodejs/unified-loader.txt`):<br>&nbsp;+ Hỗ trợ manifest nhiều file với custom `require()`.<br>&nbsp;+ VM sandbox execution context để cách ly bảo mật. | Hoàn thành |
| **Sáu** | **Access & Team Controllers** | - Xây dựng `accessController.js`: quy tắc IP whitelist/blacklist theo workspace.<br>- Xây dựng `teamController.js`: danh sách thành viên theo role hierarchy, hệ thống mời (hết hạn 7 ngày), cập nhật role, xóa thành viên. | Hoàn thành |

### 3. Kết quả đạt được

#### Kỹ thuật:
* **Controller Layer hoàn chỉnh:** Tất cả 10 controllers đã triển khai với đầy đủ CRUD và thao tác chuyên biệt.
* **Pipeline mã hóa end-to-end:**
    1. File upload → nén (gzip) → mã hóa (AES-256-GCM) → lưu trữ.
    2. User yêu cầu script → ECDH handshake → dẫn xuất shared secret → script mã hóa bằng session key → gửi tới client.
    3. Client loader giải mã bằng session key → thực thi trong sandbox.
* **Hệ thống Loader:** Cả Python và Node.js loader hoạt động với:
    * Trao đổi khóa an toàn (X25519 ECDH).
    * Lấy vân tay phần cứng phía client (MAC, hostname, CPU).
    * Thực thi script minh bạch với xử lý lỗi.
* **Quản lý License:** Vòng đời license hoàn chỉnh — tạo, tạo hàng loạt, khóa HWID, hết hạn, xuất dữ liệu.

#### Bảo mật:
* **Defense in depth:** Mã hóa at-rest (AES-256-GCM) + mã hóa in-transit (ECDH + AES) + kiểm soát truy cập (IP/HWID/license) + rate limiting.
* **Không lộ plaintext:** Nội dung script không bao giờ được gửi dưới dạng chưa mã hóa qua mạng.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** ECDH key exchange thêm độ trễ (~100ms mỗi lần handshake) cho quá trình loader.
* **Giải pháp:** Chấp nhận đánh đổi — bảo mật quan trọng hơn độ trễ nhỏ cho nền tảng bảo vệ code. Handshake chỉ xảy ra 1 lần mỗi phiên.

### 5. Bài học rút ra
* AES-256-GCM cung cấp cả bảo mật và toàn vẹn (authenticated encryption), loại bỏ bước HMAC riêng.
* X25519 ECDH nhanh hơn đáng kể so với RSA cho key exchange mà vẫn đảm bảo mức bảo mật tương đương (128-bit security level).
* Thiết kế loader cho nhiều ngôn ngữ cho thấy tầm quan trọng của API contract nhất quán giữa các triển khai.

### 6. Bước tiếp theo
* Bắt đầu migration sang AWS — thiết kế kiến trúc serverless.
* Tạo SAM/CloudFormation template.
* Chuyển đổi lớp dữ liệu SQLite sang DynamoDB.


