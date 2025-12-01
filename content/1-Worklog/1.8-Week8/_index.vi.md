---
title: "Nhật ký tuần 8"
weight: 8
chapter: false
pre: "<b>1.8.</b>"
---

## 🎯 Mục tiêu tuần 8
- Học DynamoDB và mô hình NoSQL.
- Thiết kế bảng sự kiện cho Aurora Calendar.
- Viết Lambda CRUD cho sự kiện.
- Tích hợp EventBridge làm lịch nhắc nhở.

---

## 📅 Công việc đã thực hiện

| Ngày | Nội dung công việc | Tài liệu |
|------|---------------------|----------|
| **Thứ 2** | Tìm hiểu DynamoDB, PK/SK, mô hình NoSQL | https://youtu.be/y99YGaQjgxQ |
| **Thứ 3** | Tạo bảng DynamoDB: PK=userId, SK=eventId | — |
| **Thứ 4** | Viết Lambda CRUD xử lý sự kiện | https://youtu.be/JIbIYZIeLqU |
| **Thứ 5** | Nghiên cứu EventBridge Scheduler | https://youtu.be/eI3W6CXYhYw |
| **Thứ 6** | Tạo lịch nhắc nhở: EventBridge → Lambda | — |

---

## 🧠 Kiến thức tiếp thu
- So sánh SQL vs NoSQL.
- Cấu trúc khóa Partition & Sort Key.
- Luồng xử lý của Lambda.
- Lịch thực thi định kỳ với EventBridge.

---

## 🛠 Kỹ năng thực hành
- Thiết kế bảng DynamoDB tối ưu.
- Viết API CRUD dùng Lambda.
- Kết nối EventBridge Scheduler cho các reminders.
- Theo dõi log trong CloudWatch.

---

## ✔️ Tổng kết tuần 8
Backend Aurora Calendar đã hoàn thiện phần API & scheduling logic cho các sự kiện.
