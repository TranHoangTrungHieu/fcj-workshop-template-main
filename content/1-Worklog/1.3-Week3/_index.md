---
title: "Week 3 Worklog"
date: "2025-09-23T19:53:52+07:00"
weight: 3
chapter: false
pre: "<b> 1.3. </b>"
---

## Week 3 Objectives
- Understand EC2 instance types, AMIs, EBS Storage, and Instance Metadata.
- Practice launching, configuring, and managing EC2 instances.
- Learn Auto Scaling Group (ASG) and Load Balancer basics.
- Build an S3 Static Website and explore CloudFront integration.

---

## Tasks Completed

| Day | Task Description | Start | End | Reference |
|-----|------------------|--------|--------|-----------|
| **Monday** | Learned EC2 fundamentals, AMI, Instance Types, EBS vs Instance Store | 09/22/2025 | 09/22/2025 | FCJ Videos 72–80 |
| **Tuesday** | Practiced EC2 setup: Security Groups, Key Pairs, User Data | 09/23/2025 | 09/23/2025 | FCJ Videos 81–85 |
| **Wednesday** | Explored Auto Scaling Group (ASG) and Load Balancer | 09/24/2025 | 09/24/2025 | FCJ Videos 86–90 |
| **Thursday** | Built S3 Static Website + enabled Versioning & Lifecycle | 09/25/2025 | 09/25/2025 | FCJ Videos 91–97 |
| **Friday** | Integrated S3 with CloudFront for global content delivery | 09/26/2025 | 09/26/2025 | FCJ Videos 98–102 |

---

## Knowledge Gained

### 🔸 EC2 Compute Concepts
- AMI, Instance Types (General, Compute, Memory optimized).
- EBS Volumes: gp3, io2, throughput concepts.
- User Data for automation on boot.
- Instance Metadata & IMDSv2.

### 🔸 Auto Scaling & Load Balancing
- Launch Template vs Launch Configuration.
- Scaling policies: Target Tracking, Simple Scaling.
- Application Load Balancer (ALB) routing & health checks.

### 🔸 S3 Static Website
- Hosting HTML/JS/CSS directly on S3.
- Enable Versioning & Lifecycle rules.
- Block Public Access settings.

### 🔸 CloudFront CDN
- How CDN caches content globally.
- Origin Access Control (OAC) to protect S3.
- Cache Behaviors & Invalidation.

---

## Practical Skills Acquired
- Launched EC2 instances using Launch Template.
- Configured User Data scripts for automated setup.
- Built a functional Auto Scaling Group with ALB.
- Deployed a static website on S3.
- Connected S3 → CloudFront to increase performance & security.

---

## Summary of Week 3
This week strengthened my understanding of compute services and taught me how to automate scaling and build production-level static websites using S3 + CloudFront. These skills are essential before learning deeper storage and migration services in Week 4.

---
