---
title: "Sự kiện 4"
date: 2026-04-11
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# Sự kiện 4: AWS Networking, Bảo mật và Quản lý Truy cập & Danh tính

### Thông tin sự kiện
| | |
|:---|:---|
| **Ngày & Giờ** | 11 Tháng 4, 2026, 9:00 sáng |
| **Địa điểm** | Hội trường Academy, Đại học FPT |
| **Vai trò** | Người tham dự |

### Mục tiêu tham dự

- Hiểu các khái niệm cốt lõi trong AWS về networking, bảo mật và quản lý danh tính
- Học cách thiết kế kiến trúc cloud an toàn và có khả năng mở rộng
- Nắm vững các best practices của IAM và các thành phần networking
- Khám phá các dịch vụ bảo mật của AWS và ứng dụng của chúng

### Mô tả sự kiện

Buổi workshop này cung cấp cái nhìn tổng quan về các khái niệm cốt lõi trong AWS, tập trung vào networking, bảo mật và quản lý truy cập.

Nội dung buổi học giúp người tham gia hiểu cách thiết kế kiến trúc cloud an toàn và có khả năng mở rộng bằng cách kết hợp các thành phần mạng, cơ chế kiểm soát truy cập và các dịch vụ bảo mật trong AWS.

---

## Nội dung chính

### 1. Identity & Access Management (IAM)

Workshop giới thiệu **AWS IAM**, một dịch vụ dùng để kiểm soát quyền truy cập vào tài nguyên AWS.

#### Khái niệm chính

- Quản lý **user, group và role**
- Kiểm soát **xác thực (authentication)** và **phân quyền (authorization)**
- Áp dụng quyền thông qua **policies**

#### Best Practices

- Áp dụng nguyên tắc **least privilege (cấp quyền tối thiểu)**
- Không sử dụng tài khoản root cho các thao tác hằng ngày
- Bật **MFA (xác thực đa yếu tố)**
- Thay đổi thông tin xác thực định kỳ
- Hạn chế sử dụng access key lâu dài

#### Nội dung nâng cao

- **Single Sign-On (SSO):** Đăng nhập một lần cho nhiều hệ thống
- **Service Control Policies (SCP):** Định nghĩa quyền tối đa trên các tài khoản
- **Permission Boundaries:** Giới hạn quyền cho các user/role cụ thể

---

### 2. AWS Networking

Phần này tập trung vào cách hoạt động của networking trong AWS thông qua **VPC (Virtual Private Cloud)**.

#### Các Thành phần Cơ bản

- **VPC & CIDR:** Định nghĩa dải địa chỉ mạng
- **Subnets:** Chia nhỏ mạng thành các segment
- **Internet Gateway (IGW):** Cho phép truy cập Internet
- **Route Tables:** Kiểm soát định tuyến traffic

#### NAT Gateway

- Cho phép các instance riêng truy cập Internet
- Ngăn chặn traffic từ Internet vào
- Sử dụng **cơ chế SNAT và PAT**

#### Các Lớp Bảo mật

- **Security Group (SG):**
  - Hoạt động ở cấp instance
  - Stateful
  - Chỉ quy tắc cho phép

- **Network ACL (NACL):**
  - Hoạt động ở cấp subnet
  - Stateless
  - Hỗ trợ quy tắc cho phép & từ chối

---

### 3. Các Dịch vụ Bảo mật của AWS

Workshop cũng giới thiệu các dịch vụ bảo mật quan trọng của AWS:

#### AWS WAF (Web Application Firewall)

- Bảo vệ ứng dụng khỏi các cuộc tấn công như:
  - SQL Injection
  - Cross-Site Scripting (XSS)
- Lọc các yêu cầu HTTP/HTTPS
- Có thể triển khai trên CloudFront, ALB, API Gateway

#### AWS Shield

- Bảo vệ chống lại **các cuộc tấn công DDoS**
- Hai phiên bản:
  - Standard (miễn phí)
  - Advanced (bảo vệ nâng cao)

#### AWS Network Firewall

- Cung cấp bảo vệ ở cấp mạng bên trong VPC
- Hỗ trợ:
  - Lọc stateful & stateless
  - Ngăn chặn xâm nhập

#### AWS Firewall Manager

- Quản lý bảo mật tập trung
- Tự động áp dụng các quy tắc bảo mật trên nhiều tài khoản
- Đơn giản hóa quản trị bảo mật đa tài khoản

---

## Những điểm chính rút ra

Từ buổi workshop này, tôi đã học được:

- IAM là điều thiết yếu để quản lý quyền truy cập an toàn vào tài nguyên AWS
- Các thành phần networking như VPC, Subnet và NAT Gateway tạo thành nền tảng của kiến trúc cloud
- Bảo mật phải được triển khai ở nhiều lớp (ứng dụng, mạng và kiểm soát truy cập)
- AWS cung cấp các dịch vụ tích hợp để bảo vệ hệ thống khỏi các mối đe dọa phổ biến
- Áp dụng các best practices có thể cải thiện đáng kể bảo mật và độ tin cậy của hệ thống
- Phương pháp bảo vệ theo chiều sâu (defense in depth) là rất quan trọng cho bảo mật doanh nghiệp

---

## Trải nghiệm cá nhân

Sự kiện này giúp tôi hiểu sâu hơn cách các thành phần khác nhau trong AWS hoạt động cùng nhau để xây dựng một hệ thống an toàn.

Tôi thấy các phần về IAM và networking đặc biệt hữu ích, vì chúng có liên quan trực tiếp đến dự án hiện tại của tôi khi làm việc với APIs, xác thực và hạ tầng cloud.

Ngoài ra, việc tìm hiểu về các dịch vụ bảo mật của AWS đã cho tôi sự tự tin hơn trong việc thiết kế các hệ thống có thể xử lý các thách thức bảo mật trong thế giới thực.

Kiến thức về bảo mật đa lớp và các best practices sẽ vô cùng quý giá khi thiết kế kiến trúc AWS của nền tảng GuardScript.

---

## Kết luận

Buổi workshop này cung cấp nền tảng vững chắc về AWS networking, bảo mật và quản lý danh tính.

Nó đã nâng cao khả năng của tôi trong việc thiết kế các hệ thống cloud an toàn, có khả năng mở rộng và hiệu quả, đồng thời tăng cường sự hiểu biết tổng thể về kiến trúc AWS.

Cách tiếp cận bảo mật tích hợp—kết hợp các cơ chế bảo mật ở cấp mạng, cấp ứng dụng và kiểm soát truy cập—là thiết yếu để xây dựng các giải pháp cấp doanh nghiệp đáp ứng các yêu cầu bảo mật hiện đại.
