---
title: "Các bài blogs đã dịch"
date: "2025-09-09T19:53:52+07:00"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---
Tại đây là phần liệt kê và giới thiệu ngắn gọn về các blogs mà em đã dịch.

---

### [Blog 1 – Tầm quan trọng của mã hóa và cách AWS hỗ trợ](3.1-Blog1/)

Blog này giải thích vai trò cốt lõi của **mã hóa (encryption)** trong chiến lược bảo mật dạng phòng thủ nhiều lớp (defense-in-depth).  
Nội dung tập trung vào:

- Cách mã hóa hoạt động và lý do cần bảo vệ khóa (key management).  
- Giải pháp mã hóa của AWS: **AWS KMS**, **AWS CloudHSM**, **External Key Store (XKS)**.  
- Mã hóa khi lưu trữ (at rest), khi truyền tải (in transit) và khi đang sử dụng (cryptographic computing).  
- Hỗ trợ PQC – **mã hóa hậu lượng tử** để chuẩn bị cho tương lai máy tính lượng tử.  
- Tổng quan về S3 default encryption, EBS envelope encryption và memory encryption trên chip Graviton.

---

### [Blog 2 – Chiến lược tăng khả năng phục hồi mạng & duy trì hoạt động trên AWS](3.2-Blog2/)

Blog này tập trung vào **business continuity** và **cybersecurity resilience** cho các tổ chức thuộc khu vực công.  
Nội dung bao gồm:

- Ứng dụng **NIST Cybersecurity Framework 2.0**, **AWS Well-Architected**, và **AWS Security Reference Architecture**.  
- Tại sao cần **multi-account strategy**, **IAM Identity Center**, và quản lý credential an toàn.  
- Xây dựng hạ tầng bằng **Infrastructure as Code (IaC)**: CloudFormation, CDK, SAM, Terraform.  
- Thiết lập **recovery accounts**, khôi phục theo AZ-ID nhất quán, hoặc khôi phục đa vùng (multi-Region recovery).  
- Chiến lược sao lưu bằng **AWS Backup**, kiểm thử tự động, immutable backups và kiểm thử toàn bộ workload.

---

### [Blog 3 – Thiết kế mô hình tích hợp serverless cho LLMs](3.3-Blog3/)

Blog này khám phá cách tích hợp **LLMs** vào ứng dụng thông qua kiến trúc **serverless**.  
Các nội dung chính:

- Gọi trực tiếp **Amazon Bedrock** từ **AWS Lambda** và xử lý timeout, streaming response.  
- Xây dựng **prompt chaining** bằng **AWS Step Functions** để tránh giới hạn 15 phút của Lambda.  
- Chạy nhiều tác vụ LLM song song (parallel execution) để giảm thời gian phản hồi đến 37%.  
- Tích hợp **cache** với DynamoDB / ElastiCache để giảm chi phí và tăng hiệu suất.  
- Tối ưu RAG workflows & lựa chọn mô hình nền tảng phù hợp cho yêu cầu AI tạo sinh.

---
 
