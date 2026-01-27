---
title: "Tuần 3: Mạng & Bảo mật Hạ tầng (Networking & Infrastructure Security)"
date: 2026-01-19
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### 1. Mục tiêu

* **Làm chủ Network:** Hiểu sâu về kiến trúc mạng lõi của AWS bao gồm VPC, chia mạng con (subnetting) và các ranh giới bảo mật mạng (Security Groups vs NACLs).
* **Nền tảng Hạ tầng:** Cấu hình Internet Gateways (IGW) và NAT Gateways để quản lý lưu lượng mạng cho dự án "Website Security Baseline Assessment Platform".
* **Nâng cao AI/NLP:** Hoàn thành chuỗi chuyên sâu về NLP bằng việc làm chủ các mô hình chuỗi (Sequence Models) để hỗ trợ tích hợp AI cho dự án trong tương lai.

### 2. Chi tiết công việc tuần

| Ngày | Nhiệm vụ chính | Chi tiết | Trạng thái | Liên kết / Bằng chứng |
|:---:|:---|:---|:---:|:---|
| **Thứ 2** | **Cốt lõi về Networking** | - **VPC Deep Dive:** Nghiên cứu các khái niệm VPC, khối CIDR và Subnetting (Public vs. Private).<br>- **Kết nối:** Cấu hình Internet Gateway (IGW) cho truy cập công khai và NAT Gateway cho các instance riêng tư.<br>- *Nguồn: Chương trình học Tuần 3.* | Hoàn thành | \ |
| **Thứ 3** | **Chứng chỉ NLP** | - Hoàn thành khóa học cuối cùng của chương trình chuyên sâu:<br>&nbsp;**Natural Language Processing with Sequence Models**.<br>- Bao gồm các kiến thức về RNNs, LSTMs và GRUs cho xử lý văn bản nâng cao. | Hoàn thành | [Link chứng chỉ](https://www.coursera.org/account/accomplishments/verify/MKFJD7RKYZC0) |
| **Thứ 4** | **AWS Specialization** | - Tiếp tục khóa **"AWS Fundamentals Specialization"** trên Coursera.<br>- Tập trung vào các module liên quan đến dịch vụ cốt lõi và khái niệm bảo mật của AWS. | Đang thực hiện | [Link khóa AWS Fundamentals Specialization](https://www.coursera.org/programs/fptu-spring-2026-6010y/specializations/aws-fundamentals?source=search) |
| **Thứ 5** | **Hạ tầng Dự án** | - Đánh giá các yêu cầu mạng cho **Website Security Baseline Assessment Platform**.<br>- Thảo luận với team *TheBois* về cách cô lập engine quét lỗ hổng bằng VPC để đảm bảo an toàn. | Hoàn thành | \ |
| **Thứ 6** | **Bảo mật Mạng** | - **Các lớp bảo mật:** Phân tích sự khác biệt giữa Security Groups (Stateful - Có trạng thái) và NACLs (Stateless - Không trạng thái).<br>- **Thực hành Lab:** Thiết lập môi trường VPC bảo mật để chuẩn bị cho việc triển khai dự án sau này. | Hoàn thành | \ |

### 3. Kết quả chính (Deliverables)

#### Kỹ thuật & Thực hành:
* **Kiến trúc VPC:** Đã thiết kế thành công một VPC tùy chỉnh với các subnet public/private, đảm bảo sơ đồ mạng an toàn.
* **Quản lý lưu lượng:** Triển khai Route Tables, IGW và NAT Gateways để kiểm soát hiệu quả lưu lượng vào/ra (inbound/outbound).
* **Tư duy Bảo mật:** Phân biệt rõ ràng các trường hợp sử dụng cho Security Groups (cấp độ instance) so với NACLs (cấp độ subnet).

#### Dự án (Team TheBois):
* **Chiến lược Hạ tầng:** Đồng bộ thiết lập mạng với nhu cầu của **Website Security Baseline Assessment Platform** — đảm bảo công cụ quét hoạt động trong môi trường được kiểm soát, tránh việc lộ thông tin ngoài ý muốn trong quá trình kiểm tra lỗ hổng.

#### Chứng chỉ & Học tập:
* **Hoàn thành Coursera:** Đạt chứng chỉ từ DeepLearning.AI:
    * *Natural Language Processing with Sequence Models*
    * *(Đây là dấu mốc hoàn thành toàn bộ chương trình NLP Specialization)*

### 4. Vấn đề & Giải pháp
* **Vấn đề:** Nhầm lẫn giữa cơ chế stateful (của Security Groups) và stateless (của NACLs) trong quá trình thiết lập bài Lab.
* **Giải pháp:** Thực hiện kiểm tra kết nối (ping) để quan sát cách lưu lượng trả về được xử lý, qua đó làm rõ việc SG tự động cho phép lưu lượng phản hồi còn NACL thì không.