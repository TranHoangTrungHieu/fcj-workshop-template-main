---
title: "Blog 2 "
date: "2025-09-09T19:53:52+07:00"
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---


# Proactive Strategies to Improve Network Resilience and Maintain Business Continuity on AWS  
**Authors:** Devin Gordon & Henrik Balle  
**Published:** July 11, 2025  
**Categories:** Best Practices, Disaster Response, Public Sector, Security, Identity & Compliance

---

Amazon Web Services (AWS) recommends that organizations prepare to recover their workloads in the event of cybersecurity incidents or business continuity disruptions—such as technical failures or natural disasters.

This article provides guidance and recommended strategies for public sector organizations to leverage AWS infrastructure in order to build highly resilient cloud-based systems. AWS encourages its customers to:

- Use cybersecurity standards and AWS architectural best practices.  
- Implement a multi-account environment.  
- Use Infrastructure as Code (IaC) to deploy environments and workloads.  
- Prepare a recovery account in a separate Availability Zone (AZ) or Region.  
- Store application code, IaC templates, configuration files, and dependencies in the recovery account.  
- Build a backup strategy that replicates data to the recovery account.  
- Implement automated unit and full workload testing within the recovery account.

---

# Use a Recognized Cybersecurity Framework

As cybersecurity threats such as ransomware continue to increase, public sector organizations are turning to frameworks like the **NIST Cybersecurity Framework (CSF) 2.0** for guidance on managing cybersecurity risks.

Although CSF organizes cybersecurity outcomes into six functions:

- Govern  
- Identify  
- Protect  
- Detect  
- Respond  
- Recover  

…it does not prescribe how these outcomes must be achieved.

To provide more concrete guidance:

- The **AWS Blueprint for Ransomware Defense** maps specific AWS services to the CSF functions.  
- The **AWS Well-Architected Framework** outlines six pillars to help architects build secure, reliable, high-performing, and efficient workloads, aligned with the **AWS Shared Responsibility Model**.  
- The **AWS Security Reference Architecture (AWS SRA)** supplements these frameworks by helping organizations design and operate AWS security services according to AWS best practices.

By combining NIST CSF and the Well-Architected Framework, this article explores essential patterns to prepare organizations for recovery from cybersecurity or disaster events.

---

# Implement a Multi-Account Strategy on AWS

AWS recommends adopting a **multi-account strategy**—a best practice for building a scalable, controlled cloud environment (landing zone).

Key enabling tools:

- **AWS Organizations**  
- **AWS Control Tower**  
- **Landing Zone Accelerator on AWS**

Benefits of a multi-account strategy include:

- Stronger workload and data isolation  
- Reduced risk of unintended lateral movement  
- Simplified automation and governance at scale

AWS also recommends centrally managing user identities using **AWS IAM Identity Center**. External identity providers can be integrated, but during recovery situations you may need to use **root credentials**—although AWS strongly advises limiting root access to essential tasks only.

Recently, AWS introduced centralized root credential management, improving overall security posture by eliminating long-lived credentials and preventing unauthorized recovery actions.

---

# Build Your AWS Infrastructure with Automation (IaC)

AWS recommends deploying all infrastructure using **Infrastructure as Code (IaC)**—a core DevSecOps principle.

Benefits of IaC:

- Faster infrastructure replication  
- Increased consistency and reproducibility  
- Fewer configuration errors  
- Built-in version control  
- Faster recovery operations

AWS provides multiple IaC options:

- **AWS CloudFormation**  
- **AWS Cloud Development Kit (AWS CDK)**  
- **AWS Serverless Application Model (AWS SAM)**  
- **Terraform** (third-party, multi-cloud support)

IaC should be parameterized using:

- Resource names  
- AWS Regions  
- IP ranges  
- Other environment-specific values  

→ enabling reuse across accounts and Regions.

IaC code should be stored in a **source code repository** (e.g., GitLab).  
Organizations can adopt automated pipelines using **AWS Prescriptive Guidance DevOps Pipeline Accelerator (DPA)**.

---

# Prepare a Recovery Location

AWS recommends creating **dedicated recovery accounts** to protect against cybersecurity incidents such as identity compromise.

Risk scenario:  
If an attacker gains root access or escalates privileges in the primary account, backups stored in that same account could also be compromised.

## Recovery Within the Same Region (AZ Recovery)

If recovering within the same Region:

- Choose an Availability Zone that is completely isolated.  
- Maintain **consistent Availability Zone IDs (AZ IDs)** across all accounts.  

AWS assigns different AZ names per account, so AZ IDs must be used to ensure the recovery AZ never overlaps with deployment AZs.

## Multi-Region Recovery

For resilience against large-scale disasters:

- Use **multi-Region recovery**, such as primary workloads in **us-east-1** and recovery in **us-east-2**.  
- At minimum, AWS recommends **backing up data to another Region**.

Cross-Region backup may require revisiting your **AWS Key Management Service (AWS KMS)** key strategy to ensure encrypted data can be decrypted in the recovery account and Region.

Note: Inter-Region data transfer costs are higher than inter-AZ transfers.

---

# Build a Backup Strategy and Implement Automated Testing

AWS recommends designing a cloud-aligned backup strategy. After preparing the recovery location, organizations can use **AWS Backup** to store workload data in the recovery account.

AWS Backup can also store:

- IaC templates  
- Infrastructure configuration data  
- Application code  
- Application configuration files  

To ensure backup integrity, AWS recommends:

- Automated testing and validation  
- Verifying that backup data can be read  
- Retaining multiple versions to mitigate ransomware risks  
- Using **AWS Backup Vault Lock** to prevent unauthorized modifications

Recovery workflows should include backups of every component required to rebuild workloads:

- IaC  
- Infrastructure configuration  
- AMIs  
- Application code  
- Application settings  

Testing should occur on a recurring basis. Organizations should periodically rebuild the entire workload in the recovery account using the stored backups and IaC templates.

Existing component, integration, or user-acceptance testing scripts can be reused for these business continuity exercises.

---

# Conclusion

By following the best practices described in this article, public sector organizations can leverage AWS capabilities to prepare for and recover from business continuity events.  
For additional guidance, contact your AWS account team or solutions architect.

---

# Authors

### **Devin Gordon**  
Principal Solutions Architect at AWS, supporting U.S. federal civilian agencies.  
Specializes in AWS security and enjoys helping customers deploy secure environments.  
Interests: travel, SCUBA diving, hiking, outdoor activities.

### **Henrik Balle**  
Principal Solutions Architect at AWS supporting the U.S. Public Sector.  
Works with customers on machine learning, security, and governance at scale.  
Interests: long-distance road biking, motorcycling, and home improvement projects.

