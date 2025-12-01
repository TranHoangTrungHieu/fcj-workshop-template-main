---
title: "Nhật ký tuần 2"
date: "2025-09-16T19:53:52+07:00"
weight: 2
chapter: false
pre: "<b>1.2. </b>"
---


## Mục tiêu của tuần 2
- Hiểu mô hình mạng ảo VPC và các thành phần liên quan.
- Nắm được cách cấu hình Subnet, Route Table, Security Group, NACL.
- Thực hành triển khai EC2 trong VPC riêng, kết nối Internet qua IGW/NAT.
- Làm quen với VPC Peering và các kiểu kết nối mạng giữa các VPC.

---

## Công việc đã thực hiện

| Ngày | Nội dung công việc | Bắt đầu | Kết thúc | Tài liệu tham khảo |
|------|---------------------|----------|----------|--------------------|
| **Thứ 2** | Tìm hiểu tổng quan VPC, Subnet, CIDR, Route Table, Security Group | 09/15/2025 | 09/15/2025 | Video 25–32 (FCJ Playlist) |
| **Thứ 3** | Thực hành tạo VPC mới, chia Subnet Public/Private, tạo Route Table | 09/16/2025 | 09/16/2025 | Video 33–44 |
| **Thứ 4** | Cấu hình Internet Gateway, NAT Gateway, chạy EC2 trong Public/Private | 09/17/2025 | 09/17/2025 | Video 45–55 |
| **Thứ 5** | Tìm hiểu DNS, Route53 Resolver, thử truy cập EC2 qua IP/Domain | 09/18/2025 | 09/18/2025 | Video 56–64 |
| **Thứ 6** | Làm bài lab VPC Peering giữa 2 VPC, cấu hình Route Table để 2 VPC giao tiếp | 09/19/2025 | 09/19/2025 | Video 65–71 |

---

## Kiến thức tiếp thu được

### 🔸 VPC & Mạng ảo AWS
- Khái niệm VPC và cách AWS tổ chức mạng ảo.
- Ý nghĩa của CIDR, Subnet Public / Private.
- Cách thức Internet Gateway và NAT Gateway hoạt động.
- Cơ chế định tuyến trong Route Table.

### 🔸 Bảo mật mạng: SG & NACL
- Security Group: Stateful Firewall, cho phép theo chiều request/response.
- Network ACL: Stateless, áp dụng theo Subnet.
- Khi nào dùng SG, khi nào dùng NACL.

### 🔸 DNS & Routing nâng cao
- Route53 Resolver
- Tạo A Record, CNAME
- Cách DNS phân giải IP cho EC2 trong Private subnet

### 🔸 VPC Peering
- Kết nối 2 VPC trong cùng/khác Region
- Các trường hợp không hỗ trợ: Transit, Overlapping CIDR
- Cập nhật Route Table để các VPC giao tiếp được

---

## Kỹ năng thực hành đạt được
- Tạo VPC chuẩn AWS với Subnet Public/Private.
- Cấu hình Route Table + Internet Gateway + NAT Gateway.
- Khởi chạy EC2 trong Public subnet và SSH vào máy.
- Khởi chạy EC2 trong Private subnet và truy cập Internet thông qua NAT.
- Thiết lập VPC Peering và kiểm tra kết nối 2 EC2 ở 2 VPC.
- Kiểm tra đường đi mạng với `ping`, `curl`, `traceroute`.

---

## Tổng kết tuần 2
Tuần 2 giúp em hiểu rõ cách AWS xây dựng mạng ảo VPC, từ đó có thể triển khai EC2 đúng chuẩn doanh nghiệp, đảm bảo private subnet an toàn và public subnet có khả năng truy cập Internet khi cần thiết. Đây là nền tảng quan trọng để sang tuần 3 triển khai EC2 nâng cao, Auto Scaling và S3/CloudFront.

---
