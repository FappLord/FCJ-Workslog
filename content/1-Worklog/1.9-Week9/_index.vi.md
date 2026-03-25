---
title: "Tuần 9: GuardScript — Migration lên AWS & Thiết kế Frontend"
date: 2026-03-16
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### 1. Mục tiêu

* **Migration AWS:** Bắt đầu chuyển GuardScript từ prototype local (Express.js + SQLite) sang kiến trúc serverless trên AWS.
* **Infrastructure as Code:** Thiết lập SAM/CloudFormation template định nghĩa Lambda, DynamoDB, S3 và CloudFront.
* **Thiết kế Frontend:** Thiết kế và xây dựng các trang frontend cho ứng dụng web GuardScript (trang chủ, trang đăng nhập/đăng ký).
* **Điều phối nhóm:** Phân chia công việc trong Team TheBois cho quá trình migration.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Lập kế hoạch migration** | - Rà soát prototype local với team và vạch ra kế hoạch migration AWS.<br>- Xác định các dịch vụ AWS cần dùng: Lambda (compute), DynamoDB (database), S3 (storage + hosting), CloudFront (CDN).<br>- Phân chia công việc: frontend (tôi phụ trách), backend migration (các thành viên khác), infrastructure setup (phối hợp chung). | Hoàn thành |
| **Ba** | **Thiết kế trang chủ** | - Thiết kế và xây dựng trang chủ GuardScript (`frontend/index.html`, `style.css`, `script.client.js`).<br>- Tạo hero section với hiệu ứng canvas binary animation.<br>- Thiết kế phần feature cards giới thiệu 6 tính năng chính: licensing, cloud loader, workspace isolation, analytics, kill switch, access policies.<br>- Thêm phần workflow steps và thanh navigation responsive. | Hoàn thành |
| **Tư** | **Thiết kế trang Auth** | - Thiết kế và xây dựng trang đăng nhập (`frontend/login/`) với hiệu ứng matrix background, form email/password và danh sách lợi ích.<br>- Thiết kế trang đăng ký (`frontend/register/`) với phong cách visual nhất quán.<br>- Triển khai navigation nhận biết trạng thái đăng nhập (ẩn/hiện nút login/register/dashboard). | Hoàn thành |
| **Năm** | **SAM Template & S3 Setup** | - Rà soát và đóng góp vào SAM template (`infra/template.yaml`).<br>- Hỗ trợ cấu hình S3 bucket cho frontend hosting với versioning và AES256 encryption.<br>- Thiết lập CloudFront distribution với Origin Access Control (OAC).<br>- Cấu hình CloudFront behaviors cho SPA routing (rewrite subpaths về `index.html`). | Hoàn thành |
| **Sáu** | **Đồng bộ team & Review DynamoDB** | - Tổ chức rà soát tiến độ team — backend migration sang DynamoDB đang đúng kế hoạch.<br>- Review thiết kế DynamoDB schema: 12 tables với Global Secondary Indexes (GSIs).<br>- Lên kế hoạch layout trang dashboard và workspace IDE cho tuần tiếp theo.<br>- Cập nhật timeline dự án và task board. | Hoàn thành |

### 3. Kết quả đạt được

#### Frontend (Đóng góp cá nhân):
* **Trang chủ (Landing Page):** Thiết kế và triển khai hoàn chỉnh:
    * Hero section với hiệu ứng binary canvas animation.
    * 6 feature cards với icon và mô tả.
    * Visualization workflow (quy trình 3 bước).
    * Navigation responsive với nhận biết trạng thái auth.
    * Phong cách visual chuyên nghiệp, dark theme.
* **Trang xác thực:** Login và Register pages:
    * Hiệu ứng matrix background animation.
    * Form validation và xử lý lỗi.
    * Ngôn ngữ visual nhất quán xuyên suốt các trang.

#### Hạ tầng (Đóng góp nhóm):
* **SAM Template:** CloudFormation template định nghĩa tất cả tài nguyên AWS:
    * `ApiFunction` — Lambda function (Node.js 20.x) với Function URL.
    * `FrontendBucket` — S3 bucket cho frontend static hosting.
    * `ContentBucket` — S3 bucket cho lưu trữ file dự án đã mã hóa.
    * `Distribution` — CloudFront CDN với OAC và SPA rewriting.
    * 12 DynamoDB tables với GSIs cho query optimization.
    * CloudWatch alarms (errors, throttles, p95 latency) và dashboard.
* **DynamoDB Migration:** Data layer chuyển từ SQLite sang DynamoDB sử dụng `DynamoDBDocumentClient`.

#### Quản lý nhóm (Đóng góp cá nhân):
* Phân chia công việc rõ ràng — ai phụ trách frontend, backend, infrastructure.
* Cập nhật theo dõi tiến độ — team đồng thuận về deliverables hàng tuần.

### 4. Vấn đề & Giải pháp
* **Vấn đề:** CloudFront SPA routing — các subpath của single-page application (ví dụ `/workspace/123`) trả lỗi 403 vì không có object S3 tương ứng.
* **Giải pháp:** Cấu hình CloudFront Functions để rewrite request URI cho các subpath (`/dashboard/*`, `/workspace/*`, `/login/*`, `/register/*`) về file `index.html` tương ứng.

### 5. Bài học rút ra
* CloudFront Origin Access Control (OAC) thay thế Origin Access Identity (OAI) cũ, cải thiện bảo mật khi phân phối nội dung S3.
* SAM template giảm đáng kể độ phức tạp triển khai — một lệnh `sam deploy` thay thế hàng chục thao tác thủ công.
* Thiết kế visual identity cho frontend sớm giúp tạo trải nghiệm người dùng nhất quán xuyên suốt.
* Phân chia task rõ ràng với documented ownership tránh trùng lặp và giúp team làm việc song song.

### 6. Bước tiếp theo
* Triển khai trang dashboard với stats, workspace grid và navigation.
* Xây dựng trang workspace IDE với file explorer, editor và project settings.
* Hoàn thành testing backend migration trên AWS.
* Bắt đầu integration testing end-to-end.


