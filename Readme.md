# 🚀 Medusa Headless Commerce on AWS ECS

This repository contains a **production-grade deployment** of Medusa an open-source headless commerce platform—running entirely on AWS infrastructure.  

✅ ECS Fargate for scalable container hosting  
✅ Amazon ECR for Docker image storage  
✅ RDS (PostgreSQL) for reliable data persistence  
✅ Redis via ElastiCache for caching and sessions  
✅ Infrastructure as Code with Terraform  
✅ CI/CD with GitHub Actions  


---

## 📁 Project Structure

```plaintext
chegurishashikanth-medusa-ecs/
├── Readme.md
├── Medusa_Localhost.docx
├── backend/
│   ├── README.md
│   ├── Dockerfile
│   ├── instrumentation.ts
│   ├── jest.config.js
│   ├── medusa-config.js
│   ├── medusa-config.ts
│   ├── package.json
│   ├── tsconfig.json
│   ├── integration-tests/
│   │   ├── setup.js
│   │   └── http/
│   │       ├── README.md
│   │       └── health.spec.ts
│   └── src/
│       ├── admin/
│       ├── api/
│       ├── jobs/
│       ├── links/
│       ├── modules/
│       ├── scripts/
│       ├── subscribers/
│       └── workflows/
├── medusa-server/
│   ├── README.md
│   ├── instrumentation.ts
│   ├── jest.config.js
│   ├── medusa-config.ts
│   ├── package.json
│   ├── tsconfig.json
│   ├── .env.template
│   ├── .env.test
│   ├── .yarnrc.yml
│   ├── integration-tests/
│   ├── src/
│   └── .github/
│       ├── dependabot.yml
│       ├── scripts/
│       │   └── wait-for-server-live.sh
│       └── workflows/
│           ├── test-cli.yml
│           ├── update-preview-deps-ci.yml
│           └── update-preview-deps.yml
├── Terraform-Files/
│   ├── ALB.tf
│   ├── ecs.tf
│   ├── main.tf
│   ├── outputs.tf
│   ├── RDS.tf
│   ├── Redis.tf
│   ├── task-definition.json
│   ├── variables.tf
│   └── vpc.tf
└── .github/
    └── workflows/
        └── deployment.yml



----

## ✨ Features

- **Headless API Platform**  
  Fully customizable commerce APIs for any frontend.

- **Production-Ready Deployments**  
  Zero-downtime deploys with ECS rolling updates.

- **Infrastructure as Code**  
  Entire AWS stack built via Terraform.

- **CI/CD Pipeline**  
  Automated builds and ECS deployments via GitHub Actions.

- **Scalable Architecture**  
  Separates server and worker tasks for efficient scaling.

---

## 🛠 How It Works

This project deploys **two separate ECS services**:

✅ **Server Mode**  
- Handles API requests
- Serves the Admin Dashboard
- `MEDUSA_WORKER_MODE=server`

✅ **Worker Mode**  
- Handles background jobs, workflows, and subscribers
- No admin dashboard
- `MEDUSA_WORKER_MODE=worker`

---

## 🚀 Deployment Process

### 1. Provision AWS Infrastructure

Go to the Terraform folder and run:

```bash
cd Terraform-Files
terraform init
terraform apply



This deploys:

VPC
ECS Cluster
Application Load Balancer
RDS PostgreSQL
Redis via ElastiCache
ECS services


 Configure GitHub Secrets
In your GitHub repository settings, add these secrets:

Name	                        Purpose
AWS_ACCESS_KEY_ID	            AWS API access key
AWS_SECRET_ACCESS_KEY	AWS     secret key
DATABASE_URL                  PostgreSQL connection string
REDIS_URL	                    Redis connection string
COOKIE_SECRET                 Secret for cookies
JWT_SECRET	                  Secret for JWT tokens




 Run the Deployment Workflow
Trigger the deploy pipeline via GitHub Actions:

Go to Actions → Deploy Medusa to ECS → Run workflow

Or set your workflow to run automatically on every push to main.




 # Medusa Backend Deployment on AWS

This project demonstrates the deployment of the **Medusa** open-source headless commerce backend using **Terraform** on **AWS ECS with Fargate**, along with a production-ready setup including PostgreSQL, Redis, and an Application Load Balancer.

---

## 🧩 Included Components

| Service              | Purpose                         |
|----------------------|----------------------------------|
| **ECS Fargate**      | Container runtime to host Medusa backend without managing servers |
| **RDS PostgreSQL**   | Persistent relational database to store product, user, and order data |
| **ElastiCache Redis**| In-memory datastore for real-time events and caching |
| **ALB**              | Application Load Balancer to route traffic to ECS tasks |

---

## 📦 Infrastructure Overview

- **Terraform** is used as Infrastructure as Code (IaC) to provision and manage the AWS resources.
- **GitHub Actions** is used for Continuous Deployment (CD) to automatically deploy updates on push to the repository.
- **Medusa backend** runs in a Docker container inside ECS Fargate, ensuring scalable, serverless container hosting.

---

## 🚀 Deployment Workflow

1. Clone this repository and configure your AWS credentials.
2. Use Terraform to provision the infrastructure:
   ```bash
   terraform init
   terraform apply


## 🚀 Local Deployment

cd backend
yarn install
yarn dev

then open this
http://localhost:9000/app


