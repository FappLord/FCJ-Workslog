---
title: "Tuần 12: GuardScript — Hoàn thiện tài liệu, kiểm thử & chuẩn bị demo"
date: 2026-03-27
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### 1. Mục tiêu

* Hoàn thiện tài liệu proposal/worklog để khớp với code và tiêu chí FCJ.
* Chốt luồng deployment end-to-end và các điểm kiểm tra vận hành.
* Bổ sung nội dung cost-awareness và cleanup cho giai đoạn demo.

### 2. Chi tiết công việc trong tuần

| Thứ | Công việc chính | Chi tiết kỹ thuật | Trạng thái |
|:---:|:---|:---|:---:|
| **Hai** | **Chuẩn hóa Proposal** | - Rà lại kiến trúc, service flow, security claims theo template IaC hiện tại.<br>- Loại bỏ các mô tả chưa có bằng chứng triển khai rõ ràng. | Hoàn thành |
| **Ba** | **Chuẩn hóa Worklog** | - Mapping các đầu việc thực tế với module code (auth, loader, license, infra).<br>- Đồng bộ cách diễn đạt theo format FCJ. | Hoàn thành |
| **Tư** | **Rà Deployment Pipeline** | - Kiểm tra quy trình SAM deploy.<br>- Kiểm tra sync frontend lên S3 và CloudFront invalidation. | Hoàn thành |
| **Năm** | **Rà Monitoring Baseline** | - Xác minh CloudWatch alarms/dashboard.<br>- Rà thông số log retention và các output vận hành. | Hoàn thành |
| **Sáu** | **Chuẩn bị Demo Checklist** | - Chốt checklist test/validation cho demo.<br>- Bổ sung checklist cleanup để kiểm soát chi phí. | Hoàn thành |

### 3. Kết quả đạt được

* Proposal được điều chỉnh để phản ánh đúng trạng thái implementation.
* Worklog được cập nhật theo hướng có đầu ra kỹ thuật cụ thể thay vì mô tả chung.
* Quy trình triển khai end-to-end được xác định rõ với SAM + CI/CD.
* Baseline monitoring đã có cơ sở (alarms/dashboard/logging) phục vụ demo và đánh giá.
* Có checklist cleanup để kiểm soát chi phí sau khi chạy workshop/demo.

### 4. Vấn đề & Giải pháp

* **Vấn đề:** Một số phần báo cáo trước đó mô tả vượt quá phạm vi đã triển khai thực tế.
* **Giải pháp:** Chuẩn hóa nội dung theo nguyên tắc “claim có bằng chứng”, đánh dấu rõ các mục cần bổ sung thông tin.

### 5. Bước tiếp theo

* Chuẩn bị bản trình bày demo theo rubric FCJ (kiến trúc, implementation, validation, cleanup).
* Bổ sung code snippets trọng tâm vào workshop/proposal.
* Tiếp tục cải thiện các mục đánh dấu **[INFO NEEDED]** trong proposal.


