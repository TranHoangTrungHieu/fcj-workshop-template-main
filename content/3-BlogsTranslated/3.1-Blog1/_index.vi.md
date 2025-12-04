---
title: "Blog 1"
date: "2025-09-09T19:53:52+07:00"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Tầm quan trọng của mã hóa và cách AWS có thể hỗ trợ  
Tác giả: Ken Beer • Ngày đăng: 12 tháng 2, 2025  
Danh mục: AWS CloudHSM, AWS KMS, AWS Wickr, Security, Identity & Compliance

---

Bài viết được cập nhật để bao gồm các dịch vụ và tính năng mới ra mắt từ sau bản gốc năm 2020.

Mã hóa (encryption) là một phần quan trọng trong chiến lược bảo mật defense-in-depth nhằm bảo vệ dữ liệu, khối lượng công việc và tài sản số. Khi tổ chức đổi mới và xây dựng lòng tin với khách hàng, họ cần đáp ứng yêu cầu tuân thủ và tăng cường bảo mật dữ liệu.

## Cách thức và lý do mã hóa hoạt động

Mã hóa sử dụng thuật toán và khóa để biến dữ liệu có thể đọc được thành ciphertext — chỉ có thể giải mã bằng khóa phù hợp.

Ví dụ:  
Hello World! → 1c28df2b595b4e30b7b07500963dc7c

Các hệ thống mã hóa mạnh phụ thuộc vào tính toán học và đảm bảo ciphertext không thể giải được bằng năng lực tính toán hiện tại nếu không có khóa.

Do đó, bảo vệ và quản lý khóa là trung tâm của mọi giải pháp mã hóa.

---

## Mã hóa trong chiến lược bảo mật

AWS áp dụng mô hình shared responsibility.  
Bạn kiểm soát quyền truy cập dữ liệu, còn AWS đảm bảo hạ tầng bảo mật bên dưới.

Mã hóa giúp giảm thiểu rủi ro khi:

- Lộ quyền truy cập  
- Lỗi cấu hình  
- Nghe lén khi truyền dữ liệu  

### AES-256 an toàn như thế nào?

AWS sử dụng AES-256, tiêu chuẩn mạnh nhất được chính phủ phê duyệt.  
Ngay cả với máy tính lượng tử trong tương lai gần, phá AES-256 vẫn bất khả thi.

---

# Yêu cầu của một giải pháp mã hóa hiệu quả

## 1. Bảo vệ khóa khi lưu trữ (Protecting keys at rest)

Giải pháp tốt cần đảm bảo:

- Khóa không bao giờ tồn tại dưới dạng plaintext ngoài phạm vi an toàn  
- Thuật toán mã hóa được triển khai chính xác  

AWS sử dụng HSM – Hardware Security Module với các cơ chế:

- Tamper detection & tamper response  
- Chứng nhận FIPS 140-2/3 Level 3  

### Hai dịch vụ HSM của AWS:

| Dịch vụ | Đặc điểm |
|--------|----------|
| AWS KMS | AWS quản lý toàn bộ cụm HSM |
| AWS CloudHSM | Bạn tự quản lý HSM riêng |

Cả hai dịch vụ hỗ trợ:

- Tạo khóa  
- Nhập khóa từ on-premises  
- Mã hóa trực tiếp hoặc mã hóa theo lớp (envelope encryption)

### Envelope Encryption

Khóa dữ liệu (DEK) mã hóa dữ liệu → DEK được mã hóa lại bằng master key trong HSM → tăng hiệu năng và giảm tải cho HSM.

---

## 2. Quản lý khóa độc lập (Independent key management)

Bạn cần tách biệt:

- Người quản trị khóa  
- Người truy cập dữ liệu mã hóa  

AWS KMS hỗ trợ:

- IAM policy phân quyền  
- Audit logs qua AWS CloudTrail  

AWS CloudHSM hỗ trợ cơ chế policy độc lập.

---

# External Key Store (XKS)

Từ năm 2022, AWS KMS hỗ trợ lưu trữ khóa trên HSM của bạn (on-prem hoặc nơi bạn chọn).  
KMS proxy yêu cầu mã hóa/giải mã đến HSM đó.

Khóa không bao giờ rời HSM của bạn.

Nhưng bạn sẽ chịu trách nhiệm:

- Tính sẵn sàng  
- Độ trễ  
- Độ bền  

Nếu mất khóa → mất dữ liệu.

---

# Audit & giám sát

- AWS KMS → CloudTrail  
- AWS CloudHSM → CloudWatch  

---

# Mã hóa dữ liệu khi lưu trữ và truyền tải

### At rest  
Dữ liệu được mã hóa bằng AES-256 trong các dịch vụ AWS, với master key lưu trong HSM.

### In transit  
AWS sử dụng TLS 1.2 hoặc cao hơn; khuyến nghị TLS 1.3.

## s2n-tls

Do hạn chế của OpenSSL, AWS đã phát triển s2n-tls:

- Nhỏ gọn  
- Dễ audit  
- Kiểm chứng bằng formal methods  
- Mã nguồn mở Apache 2.0  

---

# s2n-quic và HTTP/3

AWS phát triển s2n-quic bằng Rust cho giao thức QUIC, nền tảng của HTTP/3.  
CloudFront hỗ trợ HTTP/3 dựa trên s2n-quic.

---

# Quản lý chứng chỉ số

Hai dịch vụ giúp tự động hóa việc phát hành và xoay vòng certificate:

- AWS Certificate Manager (ACM)  
- AWS Private CA  

Khóa certificate được bảo vệ bằng KMS hoặc CloudHSM.

---

# Mã hóa dữ liệu khi đang sử dụng (Cryptographic Computing)

Ứng dụng trong:

- Federated learning  
- Multi-party computation  

AWS Clean Rooms cung cấp tính năng C3R giúp xử lý dữ liệu mã hóa mà không lộ plaintext.

---

# Máy tính lượng tử và mật mã hậu lượng tử (PQC)

Máy tính lượng tử có thể phá vỡ RSA, ECC hoặc Diffie–Hellman.  
Nhưng AES-256 vẫn an toàn.

### AWS triển khai PQC:

- ML-KEM (chuẩn NIST PQC) tích hợp vào AWS-LC  
- Hỗ trợ PQC trong s2n-tls, KMS, ACM, Secrets Manager  
- AWS Transfer Family hỗ trợ PQC SFTP  

---

# Mã hóa mọi thứ, ở mọi nơi

AWS hỗ trợ mã hóa:

- Khi lưu trữ  
- Khi truyền tải  
- Trong bộ nhớ  

S3 mã hóa mặc định object mới.  
EBS dùng envelope encryption.  
Graviton2/3 hỗ trợ always-on memory encryption.

---

# Tổng kết

AWS:

- Ưu tiên bảo mật hàng đầu  
- Cung cấp hệ sinh thái mã hóa mạnh mẽ  
- Hỗ trợ quản lý khóa linh hoạt  
- Chuẩn bị cho tương lai lượng tử  

Bạn có thể tham khảo thêm qua diễn đàn AWS KMS, AWS CloudHSM hoặc liên hệ AWS Support.

---

## Tác giả

**Ken Beer** – Giám đốc AWS KMS & Cryptography Libraries.  
**Zach Miller** – Principal Security Specialist Solutions Architect tại AWS.
