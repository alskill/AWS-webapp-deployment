# AWS-webapp-deployment
# AWS Web Application Deployment Lab

## Overview

This project demonstrates the deployment of a web application on Amazon Web Services using core AWS services.

The lab covers compute, object storage, managed databases, networking, IAM, secrets management, application deployment, logging, monitoring, and security.

The goal is to deploy a working web application on AWS and make it accessible through the internet while keeping the database and sensitive configuration protected.

---

## Architecture

```text
                         Internet
                            │
                            ▼
                    ┌───────────────┐
                    │     VPC       │
                    │  10.0.0.0/16  │
                    └───────┬───────┘
                            │
                   ┌────────▼────────┐
                   │  Public Subnet  │
                   │  10.0.1.0/24    │
                   │                 │
                   │      EC2        │
                   │  Nginx + App    │
                   └────────┬────────┘
                            │
                            │ MySQL
                            ▼
                   ┌─────────────────┐
                   │ Private Subnet  │
                   │  10.0.2.0/24    │
                   │                 │
                   │      RDS        │
                   │     MySQL       │
                   └─────────────────┘

                         ┌─────────┐
                         │   S3    │
                         │ Storage │
                         └─────────┘

                         ┌───────────┐
                         │ CloudWatch│
                         │ Monitoring│
                         └───────────┘
```

---

## AWS Services Used

| Service          | Purpose                               |
| ---------------- | ------------------------------------- |
| VPC              | Network isolation                     |
| Subnets          | Separate public and private resources |
| Internet Gateway | Internet connectivity                 |
| Route Tables     | Network routing                       |
| Security Groups  | Traffic control                       |
| IAM              | Access management                     |
| EC2              | Application server                    |
| S3               | Object/static file storage            |
| RDS              | Managed MySQL database                |
| CloudWatch       | Monitoring and logging                |
| Nginx            | Web server/reverse proxy              |

---

## Project Structure

```text
aws-web-app-deployment-lab/
│
├── README.md
│
├── 01-prerequisites/
│   └── README.md
│
├── 02-vpc-networking/
│   └── README.md
│
├── 03-iam/
│   └── README.md
│
├── 04-s3-storage/
│   └── README.md
│
├── 05-rds-database/
│   └── README.md
│
├── 06-ec2-compute/
│   └── README.md
│
├── 07-application-deployment/
│   └── README.md
│
├── 08-environment-secrets/
│   └── README.md
│
├── 09-nginx/
│   └── README.md
│
├── 10-cloudwatch-monitoring/
│   └── README.md
│
├── 11-testing-troubleshooting/
│   └── README.md
│
├── 12-cleanup/
│   └── README.md
│
├── app/
│   └── README.md
│
└── screenshots/
    └── README.md
```

---

# Lab Phases

## Phase 1 — Prerequisites

Check the local tools, AWS CLI configuration, AWS identity, region, and existing AWS resources.

[Phase 1 →](./01-prerequisites/README.md)

---

## Phase 2 — VPC Networking

Create the AWS network infrastructure:

* VPC
* Public subnet
* Private subnet
* Internet Gateway
* Route tables
* Security groups

[Phase 2 →](./02-vpc-networking/README.md)

---

## Phase 3 — IAM

Configure IAM permissions for the application and EC2 instance.

Topics:

* IAM users
* IAM roles
* Policies
* Least privilege
* EC2 roles

[Phase 3 →](./03-iam/README.md)

---

## Phase 4 — S3 Storage

Create an S3 bucket and use it for application/static files.

[Phase 4 →](./04-s3-storage/README.md)

---

## Phase 5 — RDS Database

Create a managed MySQL database.

The database will be placed in a private network and should not be directly accessible from the public internet.

[Phase 5 →](./05-rds-database/README.md)

---

## Phase 6 — EC2 Compute

Launch an EC2 Linux server.

Install:

* Java
* Maven
* Git
* Nginx

[Phase 6 →](./06-ec2-compute/README.md)

---

## Phase 7 — Application Deployment

Build and deploy the Java/Maven application onto EC2.

Application flow:

```text
GitHub
   ↓
Clone repository
   ↓
Maven Build
   ↓
JAR
   ↓
EC2
```

[Phase 7 →](./07-application-deployment/README.md)

---

## Phase 8 — Environment Variables & Secrets

Configure application settings without committing sensitive information to Git.

Examples:

```text
DB_HOST
DB_NAME
DB_USER
DB_PASSWORD
```

[Phase 8 →](./08-environment-secrets/README.md)

---

## Phase 9 — Nginx

Configure Nginx as a reverse proxy.

```text
Internet
   ↓
Port 80
   ↓
Nginx
   ↓
Java Application
   ↓
Port 8080
```

[Phase 9 →](./09-nginx/README.md)

---

## Phase 10 — CloudWatch

Configure monitoring and logging.

Monitor:

* EC2 CPU
* Application logs
* Nginx logs
* System activity

[Phase 10 →](./10-cloudwatch-monitoring/README.md)

---

## Phase 11 — Testing & Troubleshooting

Verify:

* Application availability
* Database connectivity
* S3 access
* Security groups
* Nginx
* Logs
* CloudWatch

[Phase 11 →](./11-testing-troubleshooting/README.md)

---

## Phase 12 — Cleanup

Delete the resources created during the lab to avoid unnecessary AWS charges.

[Phase 12 →](./12-cleanup/README.md)

---

# Skills Demonstrated

This project demonstrates practical knowledge of:

* Linux
* AWS
* VPC
* EC2
* S3
* RDS
* IAM
* Security Groups
* Networking
* Java
* Maven
* Nginx
* Environment Variables
* Secrets Management
* CloudWatch
* Git
* GitHub
* Application Deployment
* Cloud Security
* Troubleshooting

---

# Security Considerations

The project follows basic cloud security practices:

* Database is not publicly exposed.
* Security groups restrict network access.
* IAM permissions follow least privilege.
* Database passwords are not committed to Git.
* Sensitive configuration is stored outside source code.
* AWS resources are removed after completing the lab.

---

# Final Result

The completed project will demonstrate:

```text
Developer
    │
    ▼
GitHub
    │
    ▼
AWS EC2
    │
    ├── Nginx
    │
    └── Java Application
             │
             ├── RDS MySQL
             │
             └── S3
             
CloudWatch
    │
    └── Monitoring + Logs
```

---

# Author

**Alfia Ali**

Cloud / DevOps Engineering Lab

GitHub: https://github.com/alfi-teachs
