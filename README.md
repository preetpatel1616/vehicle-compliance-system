# 🚗 Vehicle Compliance System

A cloud-native platform that automates vehicle compliance checks by extracting license plate data from uploaded vehicle images using OCR and checking them against a compliance database. The system sends automated email notifications based on the results.

---

## 🔧 Tech Stack

- **Frontend & Backend**: Next.js (with API routes)
- **Cloud Services (AWS)**:
  - AWS Rekognition – for OCR
  - AWS Lambda – for batch processing
  - AWS SES – for email notifications
  - AWS RDS (PostgreSQL) – for storing vehicle compliance data
  - AWS S3 – for image storage
  - AWS Elastic Beanstalk – for deployment
- **Security & Deployment**:
  - JWT – for token-based authentication
  - Docker – containerization
  - GitHub Actions – CI/CD

---

## 🎯 Features

| Feature | Status | Description |
|--------|--------|-------------|
| Vehicle image upload | ✅ | Allows image submission via form |
| OCR using Rekognition | ✅ | Extracts license plate from images |
| Regex-based filtering | ✅ | Isolates valid plate numbers |
| PostgreSQL compliance check | ✅ | Verifies plate data in DB |
| SES email notifications | ✅ | Sends compliance result to user |
| JWT-based Auth | ✅ | Secures sensitive endpoints |
| Dockerized deployment | ✅ | For consistent cloud deployment |
| CI/CD (GitHub Actions) | ✅ | Tests and deploys to AWS |
| Lambda-based batch OCR | ⚙️ | Script present for processing |
| Multi-region readiness | 📝 | Deployment design prepared |
| Object detection OCR | 📝 | Future enhancement planned |

---

## 📂 Folder Overview

```bash
.
├── pages/api/                 # Next.js backend API routes
├── lib/aws/rekognition.ts     # AWS Rekognition OCR logic
├── lib/aws/ses.ts             # AWS SES logic
├── docker/                    # Dockerfiles and deployment shell scripts
├── prisma/                    # DB models and PostgreSQL schema
└── .ebextensions/             # Elastic Beanstalk configuration
```

---

## 🔍 OCR Accuracy Challenge

- **Issue**: AWS Rekognition detected irrelevant text from images.
- **Fix**: Developed custom regex-based filtering pipeline.
- **Improvement**: OCR accuracy rose from ~15% to ~50%.

---

## 📩 Email Notifications

Automated email is sent to users after compliance verification using **AWS SES**.

---

## 🛡️ Security

- JWT-based auth implemented for protected routes.
- Tokens generated post-login.
- Credentials and tokens stored in `.env` file (not committed).

---

## 🧪 Future Improvements

- Integrate object detection before OCR for better accuracy.
- Train region-specific models for localized results.

---

## 📸 Preview

_Example flow from image upload to notification:_

> *(Add screenshots or GIFs here if available in the repo)*

---

## 🚀 Deployment

```bash
# Local build and run
docker build -t vehicle-compliance .
docker run -p 3000:3000 vehicle-compliance

# CI/CD handled via GitHub Actions to Elastic Beanstalk
```

---

## 🙋‍♂️ Author

Built by [Preet Patel](https://github.com/preetpatel1616)

---

## 📄 License

MIT
