---
title: "Bản đề xuất"
date: 2026-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# GuardScript — Nền tảng Phân phối Mã nguồn An toàn
## Giải pháp AWS Serverless cho Phân phối Script Mã hóa & Quản lý License

### 1. Tổng quan Dự án

**GuardScript** là nền tảng cloud-native được xây dựng để giải quyết vấn đề tái phân phối mã nguồn trái phép. Nền tảng cung cấp cho lập trình viên và nhà phân phối phần mềm một cách an toàn để phân phối script (Python, Node.js) đồng thời duy trì toàn quyền kiểm soát ai có thể thực thi code, trên phần cứng nào và trong bao lâu.

Nền tảng được phát triển bởi **Team TheBois** như dự án chính cho chương trình thực tập FCJ 2026. Toàn bộ hệ thống chạy trên hạ tầng serverless AWS, đảm bảo tự động mở rộng, chi phí vận hành thấp và hiệu quả trả-theo-sử-dụng.

**Vai trò của tôi trong dự án** tập trung vào:
- Thiết kế và triển khai frontend website (trang chủ, dashboard, workspace IDE, trang đăng nhập/đăng ký).
- Điều phối nhóm, phân chia công việc và theo dõi tiến độ.
- Hỗ trợ cơ bản trong thiết lập hạ tầng và kiểm thử.

### 2. Mục tiêu

1. **Phân phối an toàn:** Cho phép lập trình viên phân phối script đã mã hóa chỉ có thể thực thi bởi người dùng được ủy quyền với license hợp lệ.
2. **Quản lý License:** Cung cấp vòng đời license hoàn chỉnh — tạo, tạo hàng loạt, khóa HWID, hết hạn và thu hồi (kill switch).
3. **Cách ly Workspace:** Cho phép nhiều workspace độc lập với project, thành viên, khóa mã hóa và quy tắc truy cập riêng biệt.
4. **Cộng tác nhóm:** Hỗ trợ cộng tác theo vai trò (owner, admin, editor, viewer) với onboarding qua lời mời.
5. **Triển khai Cloud-Native:** Chạy toàn bộ nền tảng trên dịch vụ serverless AWS để tiết kiệm chi phí và tự động mở rộng.
6. **Frontend chuyên nghiệp:** Cung cấp giao diện web responsive, đẹp mắt để quản lý tất cả tính năng.

### 3. Tuyên bố Vấn đề

#### Vấn đề
Các lập trình viên độc lập, studio nhỏ và giảng viên phân phối script (công cụ tự động, plugin, tài liệu đào tạo) đối mặt với thách thức chung: **một khi code được chia sẻ, nó có thể bị sao chép và tái phân phối tự do** mà không có sự đồng ý của tác giả. Các giải pháp hiện tại hoặc:
- Quá đắt (nền tảng DRM doanh nghiệp).
- Quá phức tạp (server licensing tùy chỉnh cần hạ tầng riêng).
- Chỉ hỗ trợ ngôn ngữ cụ thể (chỉ hoạt động với ngôn ngữ biên dịch, không phải ngôn ngữ thông dịch như Python hay JavaScript).

Không có giải pháp cloud-native nhẹ nào cung cấp:
- Phân phối script mã hóa cho ngôn ngữ thông dịch.
- Licensing khóa phần cứng.
- Kiểm soát truy cập và analytics theo từng project.
- Giao diện web đơn giản để quản lý mọi thứ.

#### Tác động
Không có bảo vệ code, tác giả script mất doanh thu, không có cách thực thi điều khoản sử dụng và không thể theo dõi cách code của họ được sử dụng. Điều này gây nản lòng việc chia sẻ công cụ và nội dung giáo dục giá trị.

### 4. Giải pháp Đề xuất

GuardScript giải quyết vấn đề bằng **pipeline phân phối mã hóa end-to-end**:

1. **Upload:** Tác giả upload script (file đơn hoặc multi-file project) qua web dashboard.
2. **Mã hóa:** Script được nén (gzip) và mã hóa at-rest bằng AES-256-GCM với khóa mã hóa workspace-level.
3. **License:** Tác giả tạo license key (đơn hoặc hàng loạt) với tùy chọn khóa HWID, ngày hết hạn và ràng buộc theo project.
4. **Phân phối:** End-user nhận script loader nhẹ (Python hoặc Node.js) đã cấu hình license key.
5. **Thực thi:** Loader thực hiện ECDH key exchange với server, nhận script đã mã hóa, giải mã phía client và thực thi trong sandbox.
6. **Kiểm soát:** Tác giả theo dõi thực thi, thu hồi license, chặn IP và bật/tắt project — tất cả từ dashboard.

**Tính năng chính:**
- **Cách ly workspace** — mỗi workspace có khóa mã hóa, project, team và quy tắc truy cập riêng.
- **Loader đa ngôn ngữ** — Python và Node.js loader với ECDH handshake, giải mã AES, và HWID fingerprinting.
- **Cộng tác theo vai trò** — hệ thống phân cấp owner > admin > editor > viewer với invitation system.
- **IP whitelist/blacklist** — quy tắc truy cập theo workspace.
- **Analytics thực thi** — số lần sử dụng, thời gian sử dụng cuối, logging vị trí.
- **Kill switch** — vô hiệu hóa tức thì bất kỳ project hoặc license nào.

### 5. Tổng quan Kiến trúc

Nền tảng sử dụng kiến trúc AWS serverless hoàn toàn. Tất cả dịch vụ compute, storage và database được quản lý bởi AWS, loại bỏ nhu cầu provisioning hoặc bảo trì server.

> **Lưu ý:** Sơ đồ kiến trúc chi tiết đang trong quá trình hoàn thiện. Mô tả dưới đây phản ánh hạ tầng thực tế đã triển khai như được định nghĩa trong SAM template (`infra/template.yaml`).

**Kiến trúc tổng quan:**

```
[End User / Loader] ──HTTPS──▶ [Lambda Function URL]
                                       │
                               ┌───────┴────────┐
                               │  API Router     │
                               │  (Express.js)   │
                               └───────┬────────┘
                          ┌────────────┼────────────┐
                          ▼            ▼            ▼
                    [DynamoDB]    [S3 Content]  [CloudWatch]
                    12 tables     Encrypted      Alarms &
                    + GSIs        files           Dashboard

[Browser] ──HTTPS──▶ [CloudFront CDN] ──▶ [S3 Frontend Bucket]
                      OAC + SPA rewrite    Static HTML/CSS/JS
```

**Luồng dữ liệu — Thực thi Script:**
1. Loader gửi license key + HWID đến `/api/v5/handshake`.
2. Server xác thực license, HWID, quy tắc IP và rate limits.
3. Server tạo cặp khóa X25519 tạm thời, dẫn xuất shared secret qua ECDH.
4. Server mã hóa nội dung script bằng AES-256-GCM sử dụng khóa dẫn xuất.
5. Server trả về payload đã mã hóa + public key server + chữ ký HMAC.
6. Loader dẫn xuất shared secret tương ứng, xác thực HMAC, giải mã script và thực thi.

### 6. Dịch vụ AWS Sử dụng

| Dịch vụ | Mục đích | Lý do chọn |
|:---|:---|:---|
| **AWS Lambda** | Hàm đơn xử lý tất cả API routes (Node.js 20.x) qua Function URL | Không cần quản lý server, tự động mở rộng, trả theo lần gọi. Lý tưởng cho workload biến động. |
| **Amazon DynamoDB** | Database chính — 12 tables với Global Secondary Indexes | NoSQL serverless với độ trễ mili giây đơn. GSIs cho phép query linh hoạt không cần schema migration. |
| **Amazon S3** (2 buckets) | Frontend static hosting + lưu trữ file project đã mã hóa | Object storage bền vững, tiết kiệm. Versioning cho rollback frontend. AES256 server-side encryption. |
| **Amazon CloudFront** | CDN phân phối frontend với OAC và SPA routing | Edge distribution toàn cầu, HTTPS termination, tùy chỉnh error pages, path-based rewriting cho SPA. |
| **AWS SAM / CloudFormation** | Infrastructure as Code — định nghĩa tất cả tài nguyên trong một template | Triển khai lặp lại được, hạ tầng version-controlled, tự động giải quyết dependency. |
| **AWS IAM** | Service roles và permission policies | Quyền truy cập least-privilege cho Lambda đến DynamoDB và S3. |
| **Amazon CloudWatch** | Monitoring: logs, alarms (errors, throttles, p95 latency), dashboard | Observability tập trung. Alarms kích hoạt khi có spike lỗi hoặc suy giảm hiệu năng. |

### 7. Lộ trình

| Giai đoạn | Thời gian | Hoạt động |
|:---|:---|:---|
| **Tuần 1–5** (05/01 – 06/02) | Học AWS & Lên ý tưởng | AWS cơ bản (EC2, S3, VPC, IAM, Lambda, DynamoDB), brainstorm dự án, thiết lập team, chứng chỉ. |
| **Nghỉ Tết** (07/02 – 22/02) | Nghỉ lễ | — |
| **Tuần 6** (23/02) | Thiết kế dự án | Đồng bộ sau Tết, xác định scope GuardScript, thiết kế kiến trúc, nghiên cứu crypto. |
| **Tuần 7–8** (02/03 – 14/03) | Prototype Local | Phát triển backend (Express.js + SQLite), auth, controllers, module crypto, loaders, hệ thống license. |
| **Tuần 9** (16/03) | Migration AWS | SAM template, migration DynamoDB, setup S3, thiết kế frontend landing & auth pages. |
| **Tuần 10** (23/03) | Frontend & Testing | Dashboard, workspace IDE, responsive design, integration testing. |
| **Tuần 11–12** (30/03 – 11/04) | Hoàn thiện & Bàn giao | Final testing, sửa bug, documentation, hoàn thiện sơ đồ kiến trúc, chuẩn bị báo cáo. |

### 8. Ước tính Ngân sách / Chi phí

| Hạng mục | Chi phí |
|:---|:---|
| AWS Lambda | Miễn phí (free tier / credits) |
| Amazon DynamoDB | Miễn phí (free tier / credits) |
| Amazon S3 | Miễn phí (free tier / credits) |
| Amazon CloudFront | Miễn phí (free tier / credits) |
| CloudWatch | Miễn phí (free tier / credits) |
| **Tổng chi phí ước tính** | **0 USD** |

> **Lưu ý:** Toàn bộ chi phí hạ tầng được bao phủ bởi **AWS promotional credits (200 USD)**. Dự án được thiết kế để hoạt động tốt trong giới hạn free tier cho phát triển và sử dụng production lưu lượng thấp. Không cần chi phí phần cứng hoặc dịch vụ bên thứ ba.

### 9. Đánh giá Rủi ro

| Rủi ro | Tác động | Xác suất | Giảm thiểu |
|:---|:---:|:---:|:---|
| **Hết credit** | Trung bình | Thấp | Theo dõi sử dụng với AWS Budgets và Cost Explorer. Kiến trúc dùng dịch vụ serverless trả-theo-sử-dụng, giữ chi phí tối thiểu. |
| **DynamoDB throttling** | Trung bình | Thấp | On-demand capacity mode tự động xử lý traffic spikes. GSIs được thiết kế phân bố query đều trên partitions. |
| **Loader bị reverse engineer** | Trung bình | Trung bình | ECDH key exchange đảm bảo mỗi session dùng khóa mã hóa duy nhất. Nội dung script không bao giờ cache dạng plaintext. Obfuscation loader thêm một lớp bảo vệ. |
| **Rò rỉ key/credential** | Cao | Thấp | Không lưu secrets trong code. Biến môi trường inject qua SAM template. JWT tokens có TTL 7 ngày với vô hiệu hóa khi đổi mật khẩu. |
| **CloudFront cache cũ** | Thấp | Trung bình | Cache invalidation khi deploy. Versioned S3 objects cho frontend assets. |
| **Chậm trễ điều phối nhóm** | Trung bình | Trung bình | Sync hàng tuần, tài liệu phân chia task rõ ràng, check-in hàng ngày trong giai đoạn quan trọng. |

### 10. Hướng Cải tiến Tương lai

1. **Loader thêm ngôn ngữ:** Mở rộng hỗ trợ Lua, Ruby hoặc ngôn ngữ thông dịch khác.
2. **Dashboard Analytics:** Trực quan hóa execution patterns, phân bố địa lý, tận dụng license qua biểu đồ.
3. **Webhook Notifications:** Thông báo tác giả khi license được kích hoạt, hết hạn, hoặc phát hiện hoạt động đáng ngờ.
4. **Custom Domain:** Cho phép tác giả phân phối loader từ domain thương hiệu riêng.
5. **CI/CD Pipeline:** Tự động hóa triển khai với GitHub Actions cho continuous delivery.
6. **Tích hợp Monaco Editor:** Nhúng code editor đầy đủ (Monaco) vào workspace IDE cho chỉnh sửa trên trình duyệt.
7. **Xác thực hai yếu tố:** Thêm 2FA dựa trên TOTP để tăng cường bảo mật tài khoản.
8. **Audit Logging:** Nhật ký kiểm toán toàn diện cho các use case yêu cầu compliance.

### 11. Bối cảnh Đóng góp Cá nhân

Với vai trò trưởng nhóm, đóng góp chính của tôi cho dự án này gồm:

- **Thiết kế và triển khai frontend website:** Thiết kế và xây dựng tất cả trang frontend (landing, login, register, dashboard, workspace IDE) với layout responsive, chuyển đổi theme và các thành phần tương tác.
- **Điều phối nhóm và theo dõi tiến độ:** Quản lý phân chia công việc trong Team TheBois, tổ chức sync hàng tuần, theo dõi milestones và đảm bảo phối hợp giữa phát triển frontend và backend.
- **Hỗ trợ kỹ thuật cơ bản:** Hỗ trợ các task hạ tầng cơ bản (cấu hình S3, setup CloudFront, review SAM template) nhưng không phải người chịu trách nhiệm chính cho kiến trúc bảo mật backend hoặc triển khai mã hóa — những phần này do các thành viên khác với chuyên môn sâu hơn về bảo mật đảm nhận.
