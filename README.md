# 🛒 CloudStore 2.0 – DevOps-Powered Serverless E-Commerce Platform

**CloudStore 2.0** is a production-grade online store application rebuilt from my original final project (PHP + MySQL, August 2023) into a fully serverless and secure AWS-based architecture. Designed to mirror a real-world e-commerce experience, this version prioritizes cloud-native principles, automation, security, and DevOps best practices.

> 🚀 Built to reinforce knowledge for the AWS Certified DevOps Engineer – Professional exam (Scheduled for **April 16, 2025**)

---

## 🔍 Summary

Users can register, browse items, place orders, and receive downloadable receipts via email. Admins can add/update inventory via secure tools. The application features automated CI/CD, secure resource access, accessibility testing, and multi-database workflows.

---

## 🌐 Live Demo

- **Frontend**: https://cloudstore.harrisonholt.dev
- **API**: https://api.harrisonholt.dev *(protected by Cognito)* 
- **GitHub**: [github.com/harrisonholt/cloudstore2.0](https://github.com/Harrison-Holt/CloudStore-Project.git)

---

## 🧰 Tech Stack

### 🖥 Frontend

- **React + Vite**
- **Material UI (MUI)**
- **Hosted** on **S3 + CloudFront**
- **Authenticated** with **Cognito Hosted UI**

### ☁️ AWS Services

| Layer | Services |
|-------|----------|
| API Gateway | JWT auth, connects frontend to backend |
| Lambda | Stateless backend logic for auth, orders, receipt gen |
| DynamoDB | Product catalog |
| RDS (MySQL) | Order history, relational logic |
| Cognito | User auth |
| SES | Email receipts and badges |
| S3 | Store product images and downloadable receipts (pre-signed URLs) |
| Step Functions | Order flow orchestration |
| EventBridge | Triggers Step Functions |
| CloudWatch | Logs, Alarms, Metrics |
| VPC | RDS in private subnets, secure Lambda comms |
| CodePipeline | Deploy Lambdas |
| GitHub Actions | Deploy frontend + run accessibility tests |

---

## 🛠️ Features

### 👨‍👩‍👧‍👦 User-Facing

- Cognito Registration/Login
- Browse product catalog
- Cart functionality
- Order submission
- Email receipt + shareable badge (via SES + pre-signed S3)
- View order history

### 🧪 Developer/Infra-Focused

- API Gateway JWT auth
- Event-driven backend
- Step Functions: validate → store → generate → email
- RDS isolated in VPC
- Pre-signed S3 receipts
- IAM: granular Lambda roles
- CloudWatch logs/alarms
- CI/CD with GitHub Actions + CodePipeline
- Accessibility audits with Pa11y + Lighthouse

---

## ⚙️ Architecture Diagram

```plaintext
[ React (S3 + CloudFront) ]
           |
       Cognito Auth
           ↓
   [ API Gateway (JWT) ]
           ↓
        [ Lambda ]
           ↓
     [ EventBridge ]
           ↓
   [ Step Functions ]
        ├─ Check Inventory (DynamoDB)
        ├─ Insert Order (RDS)
        ├─ Generate Receipt (S3)
        └─ Email Summary (SES)
```

---

## 🔐 Security Considerations

- Cognito user pools (OAuth2)
- API Gateway JWT authorizer
- IAM policies: least privilege (Lambda, S3, SES)
- VPC with private/public subnets
- RDS not publicly accessible
- WAF fronting CloudFront
- S3: pre-signed receipt access only

---

## 🧪 Testing & Monitoring

| Type | Tool |
|------|------|
| Accessibility | Pa11y CI, Lighthouse CI |
| Monitoring | CloudWatch Logs, Metrics, Alarms |
| CI/CD | GitHub Actions (frontend) + CodePipeline (backend) |

---

## 📦 Folder Structure

```bash
cloudstore2.0/
├── frontend/               # React + Vite + MUI
├── lambdas/                # Node.js functions
├── step-functions/         # ASL JSON/State Machine files
├── cicd/                   # GitHub workflows + CodePipeline YAML
├── infra/
│   ├── rds.sql             # RDS schema
│   ├── dynamodb-seed.json
│   └── s3-policies.json
└── README.md
```

---

## 📚 Learning Outcomes

- ✅ Mastered secure serverless design patterns
- ✅ Integrated Step Functions + EventBridge for async flows
- ✅ Hardened VPC and RDS deployments
- ✅ CI/CD pipelines for React + Lambda
- ✅ Used SES for transactional email + file delivery
- ✅ CloudWatch-based logging and alerting
- ✅ Developed with WCAG-accessibility in mind (Pa11y, Lighthouse)

---

## 📌 Next Steps

- Add product recommendation engine (based on purchase history)
- Add admin inventory UI (serverless protected admin dashboard)
- Monitor error rates via X-Ray
- Deploy secondary region for disaster recovery

---

## 📆 Timeline

- Initial version built: August 2023 (PHP/MySQL)
- Rebuilt on AWS: April-May 2025

---

## 🧑‍💻 About the Developer

**Harrison Holt**  
- BS in Computer Science | Clemson University  
- AWS Certified: Solutions Architect – Associate, Developer – Associate  
- DevOps Pro Exam: *April 16, 2025*  
- 💼 Open to cloud/backend roles in **Atlanta** or **remote**  

🔗 [Portfolio](https://harrisonholt.dev) | [LinkedIn](https://www.linkedin.com/in/harrison-holt-18a703202/) | hholt2901@gmail.com

---

## 📄 License

MIT License

---

_Last updated: April 09, 2025_
