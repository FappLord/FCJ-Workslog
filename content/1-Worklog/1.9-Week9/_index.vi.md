---
title: "Tuần 9: GuardScript — Migration lên AWS & Cải thiện UI tổng thể"
date: 2026-03-16
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### 1. Mục tiêu

* **Migration AWS:** Chuyển GuardScript từ prototype local (Express.js + SQLite) sang kiến trúc serverless trên AWS.
* **Infrastructure as Code:** Thiết lập SAM/CloudFormation template cho Lambda, DynamoDB, S3 và CloudFront.
* **Cải thiện UI tổng thể:** Nâng cấp visual design, sửa lỗi theme, hoàn thiện các tính năng frontend còn thiếu.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Lập kế hoạch migration** | - Rà soát prototype local, xác định dịch vụ AWS cần dùng: Lambda, DynamoDB, S3, CloudFront.<br>- Phân chia công việc migration cho các thành viên. | Hoàn thành |
| **Ba** | **SAM Template & UI Enhancement** | - Đóng góp vào SAM template (Lambda, S3 buckets, CloudFront, DynamoDB tables).<br>- Cải thiện UI tổng thể: spacing, colors, logo, shield icons.<br>- Sửa lỗi light theme — nhiều component hiển thị sai trong chế độ sáng. | Hoàn thành |
| **Tư** | **Workspace & License Features** | - Thêm toggle option cho workspace.<br>- Sửa lỗi license key status update và workspace creation flow.<br>- Sửa execution summary hiển thị. | Hoàn thành |
| **Năm** | **Auth Pages & Landing** | - Sửa layout trang đăng nhập/đăng ký cho responsive tốt hơn.<br>- Thêm hiệu ứng blur cho landing page. | Hoàn thành |
| **Sáu** | **Sidebar Fix & PR Review** | - Sửa toggle sidebar trong workspace.<br>- Review và merge PR#14 → PR#21 (enhance_UI, License_status, workspace_Overview, login_register). | Hoàn thành |

### 3. Kết quả đạt được

#### Hạ tầng (Đóng góp nhóm):
* **SAM Template:** CloudFormation template định nghĩa tất cả tài nguyên AWS (Lambda, S3, CloudFront, 12 DynamoDB tables với GSIs, CloudWatch alarms).
* **DynamoDB Migration:** Data layer chuyển từ SQLite sang DynamoDB.

#### Frontend (Đóng góp cá nhân):
* Nâng cấp UI: spacing, typography, bảng màu, logo mới.
* Hoàn thiện dark/light theme toggle, lưu preference qua localStorage.
* Sửa workspace toggle, license status, execution summary, auth pages layout.
* Thêm blur effect cho landing page.
* Merge 8 PRs (PR#14 → PR#21).

### 4. Vấn đề & Giải pháp
* **Vấn đề:** Light theme gây nhiều lỗi hiển thị do component chỉ thiết kế cho dark theme.
* **Giải pháp:** Rà soát CSS, thay hardcode màu bằng CSS custom properties.

### 5. Bước tiếp theo
* Kiểm thử tích hợp end-to-end.
* Hoàn thiện sơ đồ kiến trúc.
* Chuẩn bị tài liệu báo cáo.


