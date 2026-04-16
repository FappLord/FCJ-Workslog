---
title: "Sự kiện 3"
date: 2026-04-04
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Sự kiện 3: Truy cập S3 một cách an toàn từ nhiều môi trường bằng VPC Endpoints

### Thông tin sự kiện
| | |
|:---|:---|
| **Ngày & Giờ** | 4 Tháng 4, 2026, 9:00 sáng |
| **Địa điểm** | Hội trường Academy, Đại học FPT |
| **Vai trò** | Người tham dự |

### Mục tiêu tham dự

- Hiểu cách truy cập Amazon S3 một cách an toàn từ nhiều môi trường khác nhau (cloud và on-premises)
- Tìm hiểu về VPC Endpoints và vai trò của chúng trong kết nối riêng
- Khám phá các cách triển khai Gateway Endpoint và Interface Endpoint
- Thiết kế kiến trúc hybrid với quyền truy cập an toàn vào các dịch vụ AWS

### Mô tả sự kiện

Buổi workshop này tập trung vào cách truy cập Amazon S3 một cách an toàn từ nhiều môi trường khác nhau (cloud và on-premises) thông qua VPC Endpoints.

Nội dung buổi học nhấn mạnh cách các kiến trúc cloud hiện đại có thể tránh việc truyền dữ liệu qua Internet công cộng, đồng thời vẫn đảm bảo hiệu năng và tính bảo mật trong giao tiếp giữa các dịch vụ.

---

## Nội dung chính

### 1. Tổng quan về Kết nối Riêng (Private Connectivity)

Workshop giới thiệu về **AWS PrivateLink**, một giải pháp cho phép kết nối riêng giữa VPC và các dịch vụ AWS mà không cần đi qua Internet công cộng.

Các ý tưởng chính:

- Giữ toàn bộ lưu lượng trong mạng AWS
- Tăng cường bảo mật và giảm rủi ro bị lộ dữ liệu
- Đảm bảo kết nối ổn định và độ trễ thấp

---

### 2. Các loại VPC Endpoint

Hai loại endpoint chính được trình bày:

#### Gateway Endpoint

- Dùng cho **Amazon S3 và DynamoDB**
- Định tuyến traffic thông qua **route table**
- Không cần sử dụng IP public
- Giải pháp tiết kiệm chi phí để truy cập S3

#### Interface Endpoint

- Sử dụng **Elastic Network Interfaces (ENI)**
- Hỗ trợ nhiều dịch vụ AWS khác
- Sử dụng **DNS resolution**
- Phù hợp cho các hệ thống hybrid/on-premises
- Cho phép truy cập riêng từ các mạng bên ngoài

---

### 3. Truy cập S3 từ VPC

Các bước được trình bày:

- Tạo **Gateway Endpoint**
- Cấu hình route table
- Kiểm tra kết nối từ EC2 đến S3

Kết quả:

- EC2 có thể truy cập S3 một cách riêng
- Không cần Internet gateway
- Toàn bộ traffic vẫn nằm trong mạng AWS

---

### 4. Truy cập S3 từ On-Premises

Workshop cũng mô phỏng kiến trúc hybrid:

- Hệ thống on-premises kết nối với AWS thông qua VPC
- Sử dụng **Interface Endpoint**
- Cấu hình DNS cho phân giải dịch vụ

Điều này cho phép truy cập an toàn từ các hệ thống bên ngoài vào các dịch vụ AWS mà không cần phơi bày chúng ra Internet công cộng.

---

### 5. Các Chính sách VPC Endpoint

- Kiểm soát truy cập ở mức chi tiết
- Hạn chế các tài nguyên có thể được truy cập
- Tăng cường bảo mật bằng cách áp dụng nguyên tắc cấp quyền tối thiểu
- Giám sát và kiểm toán quyền truy cập endpoint

---

## Những điểm chính rút ra

Từ buổi workshop này, tôi đã học được:

- VPC Endpoints là điều thiết yếu cho kiến trúc cloud an toàn
- Có thể truy cập các dịch vụ AWS mà không sử dụng Internet công cộng
- Gateway Endpoint và Interface Endpoint phục vụ các trường hợp sử dụng khác nhau
- Kiến trúc hybrid cần thiết kế DNS và networking phù hợp
- Bảo mật có thể được tăng cường bằng cách sử dụng các chính sách endpoint
- Kết nối riêng giảm diện tích tấn công và cải thiện bảo mật tổng thể của hệ thống

---

## Trải nghiệm cá nhân

Buổi workshop này giúp tôi hiểu rõ hơn cách hoạt động của networking trong AWS, đặc biệt là trong các môi trường bảo mật và doanh nghiệp.

Tôi thấy nó rất hữu ích vì nó liên quan trực tiếp đến các hệ thống thực tế nơi bảo mật và quyền riêng tư dữ liệu là rất quan trọng.

Kiến thức có được có thể áp dụng rất tốt cho dự án hiện tại của tôi, đặc biệt là khi làm việc với các dịch vụ AWS như S3 và thiết kế kiến trúc an toàn cho nền tảng GuardScript.

---

## Kết luận

Sự kiện này cung cấp kiến thức thực tế về cách xây dựng kiến trúc an toàn và có khả năng mở rộng bằng cách sử dụng VPC Endpoints.

Nó đã tăng cường sự hiểu biết của tôi về AWS networking và cho tôi cái nhìn rõ ràng hơn về cách thiết kế các hệ thống vừa hiệu quả vừa an toàn.

Các khái niệm được học ở đây trực tiếp hỗ trợ xây dựng các giải pháp cloud cấp doanh nghiệp với mức độ phơi bày tối thiểu đối với các mối đe dọa Internet công cộng.
