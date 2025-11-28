---
title: "Proposal"
date: "2025-09-09T19:53:52+07:00"
weight: 2
chapter: false
pre: "<b> 2. </b>"
---


## **Aurora Time**

---

### **Executive Summary**
This proposal introduces **Aurora Time**, an AWS-based personal time management app designed to simplify scheduling with a clean and intuitive interface.  
It leverages **AWS Serverless** architecture to ensure scalability, reliability, and cost efficiency — providing quick ROI by minimizing infrastructure management.

---

### **Problem Statement**

#### **Current Situation**
Users struggle to manage daily commitments due to fragmented tools (notes, phone apps, calendars).  
Existing products are complex and enterprise-focused rather than for personal scheduling.

**Aurora Time** delivers a **centralized, minimal, and user-friendly solution** for managing personal events and routines.

#### **Proposed Solution**
Aurora Time uses **Amazon S3** & **CloudFront** for static web hosting and **AWS Amplify** for simplified deployment.  
**API Gateway** and **Lambda** handle backend operations, with **DynamoDB** as a fast, low-latency database.  
**Cognito** secures authentication, **EventBridge** automates reminders, and **SES** sends email alerts.

---

### **Benefits and ROI**
- **Cost:** $16 – $50/month (~$192 – $600/year)  
- **ROI:** < 6 months  
- **Advantage:** Serverless model = no 24/7 servers, ultra-low cost, scalable instantly.  

---

### **Solution Architecture**
Aurora Time employs a fully **AWS Serverless architecture** that scales from one to millions of users.  
All API calls are handled by **Amazon API Gateway**, processed via **AWS Lambda**, and stored in **Amazon DynamoDB**.  
**Amazon EventBridge** automates reminders, while **AWS Amplify** serves the UI protected by **Amazon Cognito**.

<div style="text-align:center;">
  <img src="/images/2-Proposal/aurora-architecture.jpeg"
       alt="Aurora Time AWS Serverless Architecture"
       width="850"
       style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.25); margin-top:10px;"/>
</div>


---

### **AWS Services Used**

| AWS Service | Function |
|--------------|-----------|
| **AWS Lambda** | Executes backend logic for CRUD and reminders. |
| **Amazon API Gateway** | Provides secure RESTful API endpoints. |
| **Amazon DynamoDB** | Stores user data, events, and schedules. |
| **Amazon S3 & CloudFront** | Hosts and delivers static content. |
| **Amazon EventBridge** | Triggers and manages scheduled reminders. |
| **Amazon SES** | Sends reminder emails. |
| **AWS Amplify** | Handles frontend hosting and deployment. |
| **Amazon Cognito** | Provides secure user authentication. |

---

### **Implementation Plan**

1. **Month 1 – Research & Design:** DynamoDB modeling, Serverless architecture.  
2. **Month 1 – Cost & POC:** Use Pricing Calculator, test Cognito + DynamoDB.  
3. **Month 2 – Optimization:** Tune Lambda & DynamoDB for efficiency.  
4. **Month 2–3 – Development & CI/CD:** Build Lambda, integrate CodePipeline, develop React frontend, test Beta.  

---

### **Budget Estimation**

| Service | Description | Cost (USD/month) |
|----------|--------------|------------------|
| AWS Amplify | Static web hosting | 0.35 |
| Amazon S3 | File storage & backup | 0.05 |
| CloudFront | CDN (20GB) | 1.70 |
| API Gateway | 30k requests | 0.11 |
| Lambda | 1M requests (free) | 0.00 |
| DynamoDB | 1GB data (free) | 0.11 |
| Cognito | <1000 users | 0.00 |
| SES | 500 emails | 0.05 |
| EventBridge | 100k events | 0.10 |
| CloudWatch Logs | 1GB log | 0.10 |
| CI/CD Pipeline | 20 builds | 0.00 |

**→ Total Estimated Cost:** $16 – $50/month (~$192 – $600/year)

---

### **Risk & Mitigation**

| Risk | Impact | Probability | Mitigation |
|------|---------|--------------|-------------|
| Network latency | Medium | Medium | Use CDN + local caching. |
| DynamoDB design issues | High | Medium | Conduct POC, load testing. |
| Cost overrun | Medium | Low | Enable AWS Budgets & alerts. |
| Reminder failure | High | Low | Monitor EventBridge & Lambda via CloudWatch. |

---

### **Expected Outcomes**
- Simplified personal scheduling with automated reminders.  
- Stable, low-cost, scalable Serverless system.  
- Fully deployed CI/CD pipeline within internship period.
