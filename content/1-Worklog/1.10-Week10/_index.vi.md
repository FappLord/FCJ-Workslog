---
title: "Tuần 10: GuardScript — Triển khai Frontend & Integration Testing"
date: 2026-03-23
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### 1. Mục tiêu

* **Dashboard Frontend:** Triển khai trang dashboard chính với thống kê, quản lý workspace và cài đặt người dùng.
* **Workspace IDE Frontend:** Xây dựng trang workspace IDE với file explorer, tích hợp code editor và panel cài đặt project.
* **Responsive Design:** Đảm bảo tất cả trang hoạt động tốt trên desktop, tablet và mobile với hỗ trợ light/dark theme.
* **Integration Testing:** Điều phối kiểm thử end-to-end giữa frontend và backend AWS đã triển khai.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Trang Dashboard** | - Xây dựng trang dashboard (`frontend/dashboard/`).<br>- Triển khai sidebar navigation thu gọn được với các section: Overview, Workspaces, Projects, Licenses, Access, Team, Logs, Settings.<br>- Tạo stats cards (tổng workspaces, projects, licenses, executions).<br>- Xây dựng workspace grid với nút quick-action (mở, cài đặt, xóa). | Hoàn thành |
| **Ba** | **Trang Workspace IDE** | - Xây dựng trang workspace IDE (`frontend/workspace/`).<br>- Triển khai layout 3 panel: file explorer (trái), khu vực code editor (giữa), project settings (phải).<br>- Tạo file tree component với icon folder/file và context menu.<br>- Thêm tab bar để quản lý nhiều file mở cùng lúc. | Hoàn thành |
| **Tư** | **Theme & Responsive Design** | - Triển khai dark/light theme toggle sử dụng CSS custom properties.<br>- Thêm responsive breakpoints cho mobile (hamburger menu), tablet (sidebar thu gọn), desktop (layout đầy đủ).<br>- Test tất cả trang trên nhiều kích thước viewport.<br>- Phối hợp với team về tình trạng triển khai backend. | Đang thực hiện |
| **Năm** | **Settings & Team Management UI** | - [DỰ KIẾN] Triển khai panel cài đặt người dùng (profile, đổi mật khẩu, thống kê tài khoản).<br>- [DỰ KIẾN] Xây dựng phần quản lý team (mời thành viên, quản lý role, xem logs).<br>- [DỰ KIẾN] Thêm UI loader download và ECDH handshake explorer vào trang workspace. | Dự kiến |
| **Sáu** | **Integration Testing & Sync** | - [DỰ KIẾN] Kiểm thử end-to-end: frontend ↔ Lambda API ↔ DynamoDB ↔ S3.<br>- [DỰ KIẾN] Sửa các vấn đề CORS hoặc routing phát hiện trong testing.<br>- [DỰ KIẾN] Đồng bộ team: review tình trạng deployment, lên kế hoạch Tuần 11.<br>- [DỰ KIẾN] Tiếp tục hoàn thiện sơ đồ kiến trúc. | Dự kiến |

### 3. Kết quả đạt được (Tính đến hiện tại)

#### Frontend (Đóng góp cá nhân):
* **Trang Dashboard:** Hoạt động đầy đủ:
    * Sidebar navigation với các section thu gọn được và highlight trạng thái active.
    * Stats cards hiển thị số lượng workspace, project, license và execution.
    * Workspace grid với cards hiển thị chi tiết project và quick actions.
    * Panel cài đặt: chỉnh sửa profile, đổi mật khẩu, xóa tài khoản, thống kê.
    * Dark/light theme toggle với localStorage persistence.
* **Trang Workspace IDE:** Layout 3 panel:
    * File explorer với tree navigation, drag-and-drop và context menus.
    * Tab bar quản lý file đang mở.
    * Khu vực code editor (tích hợp Monaco editor dự kiến).
    * Sidebar cài đặt project: cấu hình licensing, IP whitelist, HWID, max executions, rate limits.
    * Panel quản lý team, xem logs và quy tắc truy cập.
    * Chức năng search & replace.
* **Responsive Design:** Tất cả trang tương thích:
    * Mobile: hamburger menu, layout xếp chồng.
    * Tablet: sidebar thu gọn, panel đơn giản hóa.
    * Desktop: layout workspace IDE 3 panel đầy đủ.

#### Hạ tầng (Tình trạng nhóm):
* Backend Lambda function đã deploy và hoạt động qua Function URL.
* DynamoDB tables đã tạo với GSIs hoạt động.
* CloudFront distribution phân phối frontend từ S3.
* CloudWatch monitoring hoạt động (alarms cho errors, throttles, p95 duration).

#### Quản lý nhóm (Đóng góp cá nhân):
* Check-in hàng ngày với các thành viên về tiến độ migration.
* Sơ đồ kiến trúc đang được hoàn thiện — các component chính đã được map, đang finalize lớp chi tiết.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** Monaco editor bundle size lớn (~2MB), tăng thời gian tải trang workspace IDE.
* **Giải pháp:** Dự kiến lazy-load editor component chỉ khi mở file, và khám phá CDN-hosted Monaco để giảm bundle impact.

* **Vấn đề:** Theme toggle cần lưu preference của người dùng qua các lần navigate và session.
* **Giải pháp:** Dùng `localStorage` lưu theme đã chọn, áp dụng khi tải trang trước khi render để tránh flash of wrong theme.

### 5. Bài học rút ra
* CSS custom properties (`--var`) giúp chuyển theme đơn giản hơn nhiều so với maintain stylesheet riêng — một toggle thay đổi toàn bộ UI.
* Xây sidebar dạng component tái sử dụng cho dashboard và workspace giảm trùng lặp code.
* Layout IDE 3 panel đòi hỏi quản lý CSS grid/flexbox cẩn thận để xử lý dynamic panel resizing.
* Check-in thường xuyên trong giai đoạn deployment giúp phát hiện sớm vấn đề tích hợp.

### 6. Bước tiếp theo
* Hoàn thành các tính năng frontend còn lại (team management UI, loader explorer).
* Hoàn tất integration testing end-to-end.
* Hoàn thiện sơ đồ kiến trúc.
* Chuẩn bị finalize báo cáo worklog và nộp proposal.
* [CẦN BỔ SUNG: Kết quả integration test cụ thể và các bug phát hiện trong E2E testing]


