# [PLATFORM CONTRACT] :: v1.0

**Last Updated:** YYYY-MM-DD
**Owner:** DevOps Engineer

## 1. Overview
This document defines the interface the application must adhere to. All configuration is provided via the environment.

## 2. Environment Variables Injected by the Platform
The platform guarantees the following environment variables will be available to the application container at runtime.

| Variable Name     | Source              | Example Value (for illustration)      |
|-------------------|---------------------|---------------------------------------|
| `PORT`            | Terraform           | `8080`                                |
| `LOG_LEVEL`       | Terraform           | `INFO`                                |
| `DATABASE_URL`    | AWS Secrets Manager | `postgresql://user:pass@host:port/db` |
| `JWT_SECRET_KEY`  | AWS Secrets Manager | `super-secret-key-from-aws`           |

## 3. Exposed Services
Endpoints provided by the platform that the application can use.

| Service      | Endpoint                      | Description                               |
|--------------|-------------------------------|-------------------------------------------|
| Public API   | `${ALB_DNS_NAME}`             | The public-facing URL for the service.    |
| Internal DNS | `auth-service.local:8080`     | The service discovery name within the VPC.|
