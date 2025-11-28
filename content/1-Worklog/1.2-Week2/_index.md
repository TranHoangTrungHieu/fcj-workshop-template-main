---
title: "Week 2 Worklog"
date: "2025-09-16T19:53:52+07:00"
weight: 2
chapter: false
pre: "<b> 1.2. </b>"
---

## Week 2 Objectives
- Understand AWS Virtual Private Cloud (VPC) concepts and core networking components.
- Learn how to configure Subnets, Route Tables, Security Groups, and Network ACLs.
- Practice deploying EC2 instances inside a custom VPC using Public/Private subnets.
- Explore VPC Peering and inter-VPC connectivity scenarios.

---

## Tasks Completed

| Day | Task Description | Start | End | Reference |
|-----|------------------|--------|--------|-----------|
| **Monday** | Learned VPC fundamentals: Subnets, CIDR, Route Tables, Security Groups | 09/15/2025 | 09/15/2025 | FCJ Playlist – Videos 25–32 |
| **Tuesday** | Created a custom VPC, configured Public/Private Subnets & Route Tables | 09/16/2025 | 09/16/2025 | FCJ Playlist – Videos 33–44 |
| **Wednesday** | Configured IGW, NAT Gateway; launched EC2 in Public/Private Subnets | 09/17/2025 | 09/17/2025 | FCJ Playlist – Videos 45–55 |
| **Thursday** | Explored DNS, Route53 Resolver; tested EC2 access via IP/Domain | 09/18/2025 | 09/18/2025 | FCJ Playlist – Videos 56–64 |
| **Friday** | Completed VPC Peering lab between two VPCs and updated Route Tables | 09/19/2025 | 09/19/2025 | FCJ Playlist – Videos 65–71 |

---

## Knowledge Gained

### 🔸 AWS VPC & Networking
- Concept of VPC and how AWS organizes virtual networks.
- Understanding CIDR blocks and Public/Private subnet designs.
- How Internet Gateway (IGW) and NAT Gateway work.
- Routing logic via Route Tables.

### 🔸 Security Groups & Network ACLs
- **Security Groups:** Stateful firewalls that automatically allow response traffic.
- **Network ACLs:** Stateless rules that apply at the subnet level.
- When to use SGs vs. NACLs.

### 🔸 DNS & Name Resolution
- Route53 Resolver basics.
- Creating A and CNAME records.
- How DNS resolves private IPs for EC2 instances inside a VPC.

### 🔸 VPC Peering
- Connecting two VPCs within the same or different Regions.
- Limitations such as non-transitive routing and overlapping CIDR blocks.
- Updating Route Tables to enable cross-VPC communication.

---

## Practical Skills Acquired
- Created a production-style VPC with Public and Private Subnets.
- Configured Route Tables, IGW, and NAT Gateway.
- Launched EC2 instances in both Public and Private Subnets.
- Enabled Internet access for Private EC2 through NAT Gateway.
- Built VPC Peering connections and verified EC2-to-EC2 communication.
- Validated routing paths using `ping`, `curl`, and `traceroute`.

---

## Summary of Week 2
Week 2 provided a solid understanding of AWS VPC networking, enabling the setup of secure and scalable cloud network infrastructure. This foundational knowledge prepares me for Week 3, where I will work on EC2 Compute, Auto Scaling, and S3/CloudFront deployment.

---
