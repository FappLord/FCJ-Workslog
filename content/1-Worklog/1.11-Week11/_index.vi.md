---
title: "Tuần 11: GuardScript — Hardening bảo mật & Kiểm soát truy cập"
date: 2026-03-20
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### 1. Mục tiêu

* Hoàn thiện và rà soát luồng bảo mật loader v2/v3 trên backend AWS.
* Chuẩn hóa các chức năng quản lý license/HWID/access list theo mô hình workspace.
* Tăng khả năng quan sát hệ thống qua logging, metrics và realtime events.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết kỹ thuật | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Rà soát Loader v2** | - Kiểm tra kiểm tra chữ ký request, timestamp ±300s, nonce.<br>- Xác minh luồng mã hóa response và chữ ký phản hồi. | Hoàn thành |
| **Ba** | **Rà soát Loader v3** | - Xác minh handshake X25519, derive key và AES-GCM encryption.<br>- Kiểm tra tính toàn vẹn response signature. | Hoàn thành |
| **Tư** | **Hardening License/HWID** | - Rà soát toggle HWID lock, reset HWID.<br>- Kiểm tra điều kiện license active/expired/project binding. | Hoàn thành |
| **Năm** | **Access Control & Rate-limit** | - Kiểm tra blacklist/whitelist theo workspace.<br>- Kiểm tra giới hạn truy cập theo IP/scope và TTL cleanup. | Hoàn thành |
| **Sáu** | **Logging & Realtime** | - Rà log action theo workspace.<br>- Kiểm tra broadcast sự kiện cho workspace/user/admin channels. | Hoàn thành |

### 3. Kết quả đạt được

* Luồng execute và handshake đã được xác minh theo thiết kế bảo mật hiện tại.
* Chức năng quản lý license/HWID và access list hoạt động nhất quán trong API.
* Cơ chế giới hạn truy cập (rate-limit) hoạt động dựa trên TTL records trong DynamoDB.
* Luồng ghi log theo workspace và phát sự kiện realtime phục vụ dashboard/admin đã ổn định.

### 4. Vấn đề & Giải pháp

* **Vấn đề:** Một số claim tài liệu cũ chưa khớp implementation hiện tại (ví dụ một số dịch vụ AWS chưa có trong IaC).
* **Hướng xử lý:** Đồng bộ lại proposal để chỉ giữ nội dung có bằng chứng từ source code và template hạ tầng.

### 5. Bước tiếp theo

* Hoàn thiện tài liệu deploy end-to-end và checklist validation.
* Chuẩn bị phần cleanup/cost-awareness cho demo.
* Chốt phiên bản proposal/worklog song ngữ trước nộp.


