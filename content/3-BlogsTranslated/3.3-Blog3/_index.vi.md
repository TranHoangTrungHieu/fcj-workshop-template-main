---
title: "Blog 3"
date: "2025-09-09T19:53:52+07:00"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Thiết kế các mô hình tích hợp Serverless cho mô hình ngôn ngữ lớn (LLMs)  
**Tác giả:** Chris McPeek  
**Ngày đăng:** 04/10/2024  
**Danh mục:** Amazon Bedrock, AWS Lambda, AWS Step Functions, Serverless  

_Bài viết được đóng góp bởi Josh Hart (Principal Solutions Architect) và Thomas Moore (Senior Solutions Architect)._

---

Bài viết này khám phá các **mô hình tích hợp theo thực tiễn tốt nhất** để dùng **mô hình ngôn ngữ lớn (Large Language Models – LLMs)** trong **kiến trúc serverless**. Các phương pháp này giúp:

- Tối ưu hiệu suất  
- Giảm chi phí  
- Tăng khả năng phục hồi  
- Tận dụng AI tạo sinh (generative AI) trên AWS

---

# Tổng quan về serverless, LLM và ví dụ minh hoạ

Ngày nay, các tổ chức ở mọi quy mô tận dụng các LLM để xây dựng sản phẩm AI tạo sinh. Serverless là lựa chọn hấp dẫn nhờ:

- Không cần quản lý máy chủ  
- Tự động mở rộng  
- Trả tiền theo mức sử dụng  
- Triển khai nhanh và linh hoạt

Những công nghệ serverless phổ biến:

- **AWS Lambda**  
- **AWS Step Functions**  
- **Amazon API Gateway**  

Các ví dụ trong bài viết dùng **Amazon Bedrock**, nền tảng cung cấp API truy cập các foundation model (FMs) như Claude, Titan, Meta Llama 3… mà không cần quản lý hạ tầng.

Ngoài ra, **Amazon SageMaker** có thể dùng để huấn luyện hoặc triển khai LLM tùy chỉnh.

Ví dụ minh hoạ: dùng LLM để tạo nội dung marketing cho dòng xe SUV mới, với hình ảnh được tạo bởi **Amazon Titan Image Generator**.

---

# Gọi trực tiếp Amazon Bedrock từ AWS Lambda

Đây là mô hình serverless đơn giản nhất:  
**Lambda → Bedrock** bằng AWS SDK (boto3).

Ví dụ Python:

```python
import json
import boto3
brt = boto3.client(service_name='bedrock-runtime')

def lambda_handler(event, context):
    body = json.dumps({
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 1000,
        "messages": [{
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text":"Create a 500 word car advert..."
                },
                {
                    "type": "image",
                    "source": {"type": "base64","media_type":"image/jpeg","data": event['image']}
                }
            ]
        }]
    })

    response = brt.invoke_model(
        body=body,
        modelId='anthropic.claude-3-sonnet-20240229-v1:0',
        accept='application/json',
        contentType='application/json'
    )

    response_body = json.loads(response.get('body').read())
    return {'statusCode': 200, 'body': response_body["content"][0]["text"]}
