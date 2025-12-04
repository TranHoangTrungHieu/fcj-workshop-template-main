---
title: "Blog 2"
date: "2025-09-09T19:53:52+07:00"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Chiến lược chủ động để tăng khả năng phục hồi mạng và duy trì hoạt động kinh doanh trên AWS  
**Tác giả:** Devin Gordon & Henrik Balle  
**Ngày đăng:** 11 tháng 7, 2025  
**Danh mục:** Best Practices, Disaster Response, Public Sector, Security, Identity & Compliance

---

Amazon Web Services (AWS) khuyến nghị các tổ chức chuẩn bị sẵn sàng để khôi phục khối lượng công việc (workloads) trong trường hợp xảy ra sự cố an ninh mạng (cybersecurity incidents) hoặc các sự kiện gián đoạn hoạt động kinh doanh (business continuity events), bao gồm thảm họa kỹ thuật và thiên tai.

Bài viết này cung cấp hướng dẫn và chiến lược dành cho các tổ chức khu vực công (public sector) nhằm tận dụng cơ sở hạ tầng AWS để xây dựng các hệ thống có khả năng phục hồi cao. AWS khuyến nghị thực hiện:

- Sử dụng các khung tiêu chuẩn cho an ninh mạng & kiến trúc theo chuẩn tốt nhất.  
- Triển khai môi trường đa tài khoản (multi-account).  
- Sử dụng hạ tầng dưới dạng mã (Infrastructure as Code – IaC).  
- Chuẩn bị một tài khoản khôi phục (recovery account) nằm ở AZ hoặc Region khác.  
- Đồng bộ mã ứng dụng, mã IaC và cấu hình sang tài khoản khôi phục.  
- Xây dựng chiến lược sao lưu dữ liệu sang tài khoản khôi phục.  
- Thực hiện kiểm thử tự động ở cấp độ đơn vị và toàn bộ workload.

---

# Sử dụng một khung tiêu chuẩn đã được công nhận

Khi các sự cố an ninh mạng như ransomware ngày càng gia tăng, các tổ chức khu vực công đang hướng tới các khung tiêu chuẩn như **NIST Cybersecurity Framework (CSF) 2.0** để quản lý rủi ro hiệu quả.

Mặc dù CSF cung cấp sáu chức năng chính:

- Govern  
- Identify  
- Protect  
- Detect  
- Respond  
- Recover  

…nhưng không mô tả chi tiết cách đạt được từng chức năng.

Để có hướng dẫn cụ thể hơn:

- **AWS Blueprint for Ransomware Defense** cung cấp bảng ánh xạ giữa các dịch vụ AWS và NIST CSF.  
- **AWS Well-Architected Framework** đưa ra sáu trụ cột quan trọng để xây dựng hệ thống an toàn, hiệu năng cao và có khả năng phục hồi.  
- **AWS Security Reference Architecture (SRA)** giúp triển khai các dịch vụ bảo mật phù hợp với best practices.

Kết hợp NIST CSF và Well-Architected Framework, bài viết trình bày các mô hình thiết yếu giúp chuẩn bị cho quá trình khôi phục khi xảy ra sự cố.

---

# Triển khai chiến lược đa tài khoản trên AWS

AWS khuyến nghị sử dụng chiến lược **multi-account** như một best practice khi xây dựng môi trường cloud (landing zone).

Các công cụ hỗ trợ:

- **AWS Organizations**  
- **AWS Control Tower**  
- **Landing Zone Accelerator on AWS**

Lợi ích:

- Cô lập ứng dụng & dữ liệu.  
- Ngăn chặn di chuyển ngang ngoài ý muốn (lateral movement).  
- Tăng khả năng tự động hóa & quản lý quy mô lớn.

AWS khuyến nghị quản lý danh tính tập trung qua **AWS IAM Identity Center**.  
Dù vậy, trong tình huống khôi phục, bạn có thể cần dùng **root credentials**, nhưng chỉ khi thật sự cần thiết.

AWS gần đây cho phép **quản lý tập trung root credentials**, giúp tăng cường bảo mật và ngăn chặn khôi phục trái phép.

---

# Xây dựng hạ tầng AWS bằng tự động hóa (IaC)

AWS khuyến nghị triển khai toàn bộ hạ tầng bằng **Infrastructure as Code (IaC)** — nền tảng của DevSecOps.

Lợi ích IaC:

- Tái tạo hạ tầng nhanh chóng  
- Tăng tính nhất quán  
- Kiểm soát phiên bản  
- Giảm lỗi cấu hình  
- Đẩy nhanh tốc độ khôi phục

Các công cụ IaC của AWS:

- **AWS CloudFormation**  
- **AWS CDK** (định nghĩa hạ tầng bằng ngôn ngữ lập trình)  
- **AWS SAM** (ứng dụng serverless)  
- **Terraform** (đa nhà cung cấp)

IaC nên được phát triển với các biến như:

- Resource naming  
- AWS Region  
- IP ranges  

→ giúp tái sử dụng giữa nhiều tài khoản và Region.

Mã IaC nên được lưu trữ trong kho mã nguồn như **GitLab**.  
Kiến trúc DevSecOps có thể chuẩn hóa bằng **AWS Prescriptive Guidance DevOps Pipeline Accelerator (DPA)**.

---

# Chuẩn bị một vị trí khôi phục (Recovery Location)

AWS khuyến nghị tạo **recovery accounts** để ứng phó sự cố như compromise danh tính.

Rủi ro: nếu attacker chiếm được root hoặc nâng quyền trong tài khoản chính, bản sao lưu trong chính tài khoản đó cũng bị ảnh hưởng.

## Khôi phục trong cùng Region (AZ Recovery)

Nếu khôi phục trong cùng Region:

- Chọn **Availability Zone** hoàn toàn tách biệt.  
- Sử dụng **AZ IDs nhất quán** giữa các tài khoản để đảm bảo rằng AZ được dùng cho recovery không trùng với AZ triển khai workload.  

## Khôi phục đa Region (Multi-Region Recovery)

Để phục hồi trước thảm họa quy mô lớn:

- Nên sao lưu dữ liệu sang Region khác.  
- Ví dụ: workload ở **us-east-1**, recovery ở **us-east-2**.

Hãy đánh giá chiến lược quản lý key trong **AWS KMS** để đảm bảo dữ liệu sao lưu giải mã được ở tài khoản/Region khác.

Lưu ý: chi phí truyền dữ liệu giữa Regions cao hơn giữa AZs.

---

# Xây dựng chiến lược sao lưu & triển khai kiểm thử tự động

AWS khuyến nghị:

- Sử dụng **AWS Backup** để sao lưu dữ liệu workload sang recovery account.  
- Lưu trữ các thành phần quan trọng:  
  - IaC  
  - cấu hình hạ tầng  
  - AMIs  
  - mã ứng dụng  
  - cấu hình ứng dụng  

Để đảm bảo sao lưu luôn hoạt động:

- Triển khai quy trình kiểm thử tự động (automated testing).  
- Kiểm tra khả năng đọc sao lưu sau khi hoàn tất (read verification).  
- Lưu trữ nhiều phiên bản để có thể phục hồi phiên bản cũ nếu bị ransomware.  
- Cân nhắc dùng **AWS Backup Vault Lock** để ngăn thao tác xoá hoặc sửa trái phép.

AWS khuyến nghị kiểm thử **toàn bộ workload** trong recovery account theo chu kỳ, sử dụng:

- IaC  
- bản sao lưu  
- kiểm thử thành phần / tích hợp / UAT

→ Điều này đảm bảo hệ thống luôn sẵn sàng khôi phục khi xảy ra gián đoạn kinh doanh.

---

# Kết luận

Bằng cách tuân theo các best practices trên, các tổ chức khu vực công có thể tận dụng sức mạnh AWS để chuẩn bị cho quá trình khôi phục khi xảy ra sự cố.

Bạn có thể liên hệ đội ngũ AWS account team hoặc kiến trúc sư giải pháp để được hỗ trợ thêm.

---

# Tác giả

### **Devin Gordon**  
Principal Solutions Architect tại AWS, hỗ trợ các cơ quan dân sự liên bang.  
Chuyên về bảo mật AWS, đam mê giúp khách hàng xây dựng môi trường an toàn.  
Sở thích: du lịch, lặn biển (SCUBA), leo núi, hoạt động ngoài trời.

### **Henrik Balle**  
Principal Solutions Architect tại AWS, hỗ trợ khu vực công Hoa Kỳ.  
Làm việc với khách hàng về machine learning, security và governance at scale.  
Sở thích: đạp xe đường dài, chạy mô tô và tự làm các dự án cải tạo nhà.

