---
title: "Blog 1"
date: "2025-09-09T19:53:52+07:00"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# The Importance of Encryption and How AWS Can Help  
Author: Ken Beer • Published: February 12, 2025  
Categories: AWS CloudHSM, AWS Key Management Service, AWS Wickr, Security, Identity & Compliance

---

This article has been updated to include new AWS services and features released since the original publication in 2020.

Encryption is a key component of a defense-in-depth security strategy for protecting your data, workloads, and digital assets. As organizations innovate and build trust with their customers, they must meet critical compliance requirements and strengthen data protection.

## How and Why Encryption Works

Encryption uses an algorithm and a key to transform readable data into ciphertext — which can only be decrypted using the correct key.

Example:  
Hello World! → 1c28df2b595b4e30b7b07500963dc7c

Strong encryption systems rely on mathematical properties that make ciphertext computationally infeasible to break without the correct key.

Therefore, **protecting and managing encryption keys** is central to every secure encryption solution.

---

## Encryption as Part of Your Security Strategy

AWS uses the **shared responsibility model**.  
You control access to your data, while AWS secures the underlying infrastructure.

Encryption helps minimize risks such as:

- Excessive or misconfigured access  
- Data exposure during transmission  
- Unauthorized access at rest  

### How secure is AES-256?

AWS uses **AES-256**, a government-approved and industry-standard symmetric encryption algorithm.  
Even with future quantum computers, breaking AES-256 remains computationally infeasible.

---

# Requirements for an Effective Encryption Solution

## 1. Protecting Keys at Rest

A strong encryption solution must ensure that:

- Keys never exist in plaintext outside a protected boundary  
- Algorithms are implemented correctly and securely  

AWS uses **HSMs (Hardware Security Modules)** with:

- Tamper detection and tamper response  
- FIPS 140-2/140-3 Level 3 validation  

### Two AWS HSM-based services:

| Service | Description |
|--------|-------------|
| **AWS KMS** | AWS manages HSM clusters for you |
| **AWS CloudHSM** | You manage your own HSMs |

Both support:

- Creating keys  
- Importing keys from on-premises systems  
- Direct encryption or envelope encryption  

### Envelope Encryption

A data encryption key (DEK) encrypts your data →  
DEK is then encrypted using a master key stored in HSM →  
Improves performance and reduces load on HSMs.

---

## 2. Independent Key Management

You must separate:

- Key administrators  
- Data access administrators  

AWS KMS provides:

- Fine-grained IAM policy control  
- Key usage tracking via CloudTrail  

AWS CloudHSM provides fully independent key access policies.

---

# External Key Store (XKS)

Since 2022, AWS KMS allows customers to store KMS keys in **their own HSMs** (on-premises or chosen locations).

KMS proxies encryption/decryption requests to your HSM.  
The key material **never leaves your HSM**.

However, you become responsible for:

- Durability  
- Availability  
- Latency  
- Throughput  

Losing the key means **permanent loss of data**.

---

# Monitoring and Auditing

- **AWS KMS → CloudTrail**: logs all key usage  
- **AWS CloudHSM → CloudWatch**: streams audit events  

---

# Encrypting Data at Rest and In Transit

### At Rest  
AWS services use **AES-256** with master keys protected in HSMs.

### In Transit  
AWS uses **TLS 1.2 or higher**, with TLS 1.3 recommended.

## s2n-tls

Due to limitations in OpenSSL, AWS created **s2n-tls**:

- Lightweight  
- Easier to audit  
- Verified using formal methods  
- Open-source (Apache 2.0)  

---

# s2n-quic and HTTP/3

AWS built **s2n-quic** in Rust to support QUIC — the foundation of HTTP/3.  
Amazon CloudFront supports HTTP/3 using s2n-quic.

---

# Certificate Management

AWS simplifies issuing and rotating certificates via:

- AWS Certificate Manager (ACM)  
- AWS Private CA  

Keys used for certificates are protected via KMS or CloudHSM.

---

# Cryptographic Computing (Encrypting Data in Use)

Used for:

- Federated machine learning  
- Multi-party computation  

AWS Clean Rooms with **C3R (Cryptographic Computing for Clean Rooms)** enables data collaboration while keeping all data encrypted.

---

# Quantum Computing and Post-Quantum Cryptography (PQC)

Quantum computers may break:

- RSA  
- ECC  
- Diffie–Hellman  

But AES-256 remains secure.

### AWS Adoption of PQC

AWS has integrated **ML-KEM**, a NIST-selected PQC algorithm, into:

- AWS-LC (FIPS 140-3 validated library)  
- s2n-tls  
- AWS KMS  
- AWS Certificate Manager  
- AWS Secrets Manager  

AWS Transfer Family supports **post-quantum hybrid SFTP**.

---

# Encrypt Everything, Everywhere

AWS enables encryption:

- At rest  
- In transit  
- In memory  

Examples:

- S3 encrypts new objects by default  
- EBS uses envelope encryption  
- Graviton2/3 processors use always-on memory encryption  

As part of the **AWS Digital Sovereignty Pledge**, AWS continues investing in advanced encryption controls.

---

# Conclusion

At AWS, security is the top priority.  
AWS helps customers control how data is encrypted, managed, and protected across their entire infrastructure.  

AWS provides:

- Strong encryption technologies  
- Scalable key management  
- Compliance-ready security controls  

If you have questions, start a thread in the AWS KMS or AWS CloudHSM forums, or contact AWS Support.

---

## Authors

**Ken Beer** – Director of AWS Key Management Service (AWS KMS) and AWS Cryptography Libraries.  
He has more than seven years of experience at AWS in identity and access management, encryption, and key management.  
Before joining AWS, he led network security at Trend Micro and previously worked at Tumbleweed Communications.  
He has presented at RSA Conference, the U.S. DoD PKI User’s Forum, and AWS re:Invent.

**Zach Miller** – Principal Security Specialist Solutions Architect at AWS.  
He specializes in data protection, security architecture, applied cryptography, and secrets management.  
He works with AWS enterprise customers to help them strengthen security posture and reduce operational risk.
