# 🛒 CloudStore 2.0 – DevOps-Powered Serverless E-Commerce Platform

**CloudStore 2.0** is a production-grade online store application, redesigned from my original PHP final project into a modern, secure, and fully serverless AWS architecture.

Built to emphasize **DevOps**, **networking**, and **AWS Solution Architect best practices**, this platform handles user authentication, product browsing, order management, and digital receipt delivery with minimal operational overhead and full CI/CD automation.

---

## 🚀 Live Demo
🔗 Frontend: [cloudstore.harrisonholt.dev](https://cloudstore.harrisonholt.dev)  
🔗 API Base: [API Gateway Endpoint](https://api.harrisonholt.dev) *(secured)*

---

## 🧰 Tech Stack

### ☁️ Cloud Infrastructure (AWS)
- **Frontend**: React + Material UI → S3 + CloudFront (SSL) + Route 53
- **Backend**: API Gateway → Lambda → EventBridge → Step Functions
- **Authentication**: AWS Cognito (User Pools)
- **Databases**:
  - **DynamoDB** – Product Catalog
  - **RDS (MySQL)** – Orders
- **Storage**: S3 for product images and downloadable receipts (pre-signed URLs)
- **Notifications**: SES (order confirmations + badge)
- **Monitoring**: CloudWatch Logs, Alarms, and X-Ray
- **CI/CD**: GitHub Actions + CodePipeline + Pa11y + Lighthouse

---

## 🗺️ Architecture Diagram

```plaintext
[ React UI (S3 + CloudFront) ]
            |
     [Cognito Hosted UI]
            ↓
[ API Gateway (Token Auth) ]
            ↓
        [Lambda]
            ↓
      [EventBridge]
            ↓
     [Step Functions]
       ├── Validate Inventory (DynamoDB)
       ├── Save Order (RDS)
       ├── Generate Receipt (S3)
       └── Email Summary (SES with Pre-Signed URL)
