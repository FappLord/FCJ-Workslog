---
title: "Tự đánh giá"
date: 2026-03-26
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Tự đánh giá

Trong suốt thời gian thực tập tại **Amazon Web Services Vietnam** trong khuôn khổ chương trình **First Cloud AI Journey 2026** (05/01/2026 – 18/04/2026), tôi đã có cơ hội vận dụng và mở rộng đáng kể kiến thức về phát triển cloud-native trong một dự án thực tế.

Với vai trò là **Team Lead** của nhóm TheBois, tôi dẫn dắt toàn bộ quá trình thiết kế và triển khai **GuardScript** — nền tảng phân phối script serverless theo cơ chế loader kiểm soát truy cập, được deploy trên AWS. Công việc bao gồm thiết kế kiến trúc, phát triển backend (Node.js Lambda), hạ tầng dưới dạng code (AWS SAM / CloudFormation), triển khai bảo mật (HMAC, ECDH, AES-GCM) và tích hợp frontend.

Trong suốt chương trình, tôi liên tục thử thách bản thân trong các lĩnh vực mới: thiết kế giao thức mật mã, mô hình hóa đa bảng DynamoDB, cấu hình CloudFront behaviors và tích hợp WebSocket thời gian thực — những mảng kiến thức mà ban đầu tôi chưa có nhiều kinh nghiệm.

---

## Bảng tự đánh giá

| STT | Tiêu chí | Mô tả | Tốt | Khá | Trung bình |
|:---:|---|---|:---:|:---:|:---:|
| 1 | **Kiến thức và kỹ năng chuyên môn** | Vận dụng AWS, Node.js, thuật toán bảo mật, IaC vào dự án thực tế | ✅ | ☐ | ☐ |
| 2 | **Khả năng học hỏi** | Tiếp thu nhanh các dịch vụ và khái niệm mới (X25519 ECDH, SAM, CloudFront behaviors) | ✅ | ☐ | ☐ |
| 3 | **Chủ động** | Tự nghiên cứu, đề xuất quyết định kiến trúc, chủ động nêu vấn đề sớm | ✅ | ☐ | ☐ |
| 4 | **Tinh thần trách nhiệm** | Hoàn thành sprint tasks đúng hạn, chịu trách nhiệm với các quyết định thiết kế | ✅ | ☐ | ☐ |
| 5 | **Kỷ luật** | Tuân thủ sprint schedule và cam kết với team | ☐ | ✅ | ☐ |
| 6 | **Tính cầu tiến** | Chủ động xin feedback về kiến trúc và thiết kế bảo mật | ✅ | ☐ | ☐ |
| 7 | **Giao tiếp** | Viết tài liệu, trình bày quyết định kỹ thuật rõ ràng trong nhóm | ☐ | ✅ | ☐ |
| 8 | **Hợp tác nhóm** | Phân công công việc cho 6 thành viên, hỗ trợ unblock đồng đội | ✅ | ☐ | ☐ |
| 9 | **Ứng xử chuyên nghiệp** | Duy trì tinh thần hợp tác tôn trọng và xây dựng xuyên suốt chương trình | ✅ | ☐ | ☐ |
| 10 | **Tư duy giải quyết vấn đề** | Chẩn đoán lỗi hệ thống, lặp lại thiết kế giao thức bảo mật | ☐ | ✅ | ☐ |
| 11 | **Đóng góp vào dự án/tổ chức** | Kiến trúc sư chính và người triển khai chủ yếu của GuardScript | ✅ | ☐ | ☐ |
| 12 | **Tổng thể** | Hoàn thành nền tảng serverless đầy đủ, chất lượng production trong kỳ thực tập | ✅ | ☐ | ☐ |

---

## Những điểm cần cải thiện

1. **Kỷ luật và quản lý thời gian** — Deadline sprint được đảm bảo, nhưng khả năng ước lượng task và reserve buffer cần cải thiện cho các dự án quy mô lớn hơn.
2. **Kỹ năng truyền đạt kỹ thuật** — Có thể giải thích kiến trúc tốt trong giao tiếp 1:1, nhưng cần cải thiện việc viết tóm tắt súc tích cho đối tượng không chuyên kỹ thuật.
3. **Phân công công việc** — Với vai trò Team Lead, tôi có xu hướng tự đảm nhận quá nhiều phần implementation thay vì phân bổ đều hơn cho các thành viên.
4. **Kỷ luật về testing** — Nếu đầu tư vào automated testing (unit, integration) ngay từ đầu sẽ phát hiện nhiều edge case sớm hơn.

---

## Bài học rút ra

- Xây dựng hệ thống serverless chất lượng production đòi hỏi sự chú trọng đến IAM scoping, TTL-based cleanup và bảo mật ở mọi tầng.
- AWS SAM + CloudFormation giảm đáng kể độ phức tạp khi deploy, nhưng đòi hỏi hiểu rõ sự phụ thuộc giữa các resource.
- Tính năng real-time (WebSocket API) mang lại trải nghiệm người dùng tốt nhưng đặt ra thách thức quản lý connection state.
- Chương trình FCJ tạo ra môi trường để tôi thực sự làm chủ kỹ thuật — cơ hội hiếm có đã thúc đẩy sự phát triển của tôi rõ rệt.
