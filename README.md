🛠️ E-Commerce Microservices – DevOps CI/CD Pipeline

This repository contains a microservices-based e-commerce backend with a fully automated CI/CD pipeline implemented using GitHub Actions, Terraform, and Azure Kubernetes Service (AKS).

The project demonstrates modern DevOps practices: automated testing, quality and security scanning, containerization, staging deployment, production deployment, and supply chain transparency with SBOM generation.

🚀 Features Implemented
🔹 CI Pipeline (ci.yaml)

Runs unit tests with pytest for Product, Order, and Customer services.

Performs SonarQube analysis for code quality.

Executes Snyk vulnerability scans.

Builds Docker images for all services.

Pushes images to Azure Container Registry (ACR).

Generates SBOMs with Syft and scans for vulnerabilities with Grype.

🔹 Staging Deployment (staging.yaml)

Provisions infrastructure dynamically with Terraform.

Deploys microservices to staging AKS environment.

Runs acceptance tests using Postman/Newman.

Destroys staging environment automatically after validation.

🔹 Production Deployment (prod.yaml)

Deploys CI-tested images to production AKS cluster.

Dynamically injects image tags into Kubernetes manifests.

Performs smoke tests to verify service availability.

📂 Project Structure
├── backend/
│   ├── product_service/
│   ├── order_service/
│   ├── customer_service/
│   └── tests/
├── infra/                # Terraform configuration
├── k8s/                  # Kubernetes manifests
│   ├── product-service.yaml
│   ├── order-service.yaml
│   ├── customer-service.yaml
│   ├── configmaps.yaml
│   ├── secrets.yaml
│   └── databases.yaml
├── .github/workflows/
│   ├── ci.yaml
│   ├── staging.yaml
│   └── prod.yaml
└── README.md

🛠️ Tools & Technologies

Languages & Frameworks: Python, FastAPI, pytest

Version Control & CI/CD: GitHub Actions

Containerization: Docker, Azure Container Registry

Infrastructure as Code: Terraform

Orchestration: Kubernetes (AKS)

Testing: pytest, Postman/Newman

Security & Quality: SonarQube, Snyk, Syft, Grype

🔑 Required GitHub Secrets

Add the following secrets to your repository for pipelines to work:

Secret	Description
AZURE_CREDENTIALS	JSON output of az ad sp create-for-rbac (for login)
AZURE_CLIENT_ID	Service Principal App ID
AZURE_CLIENT_SECRET	Service Principal password
AZURE_TENANT_ID	Azure Tenant ID
AZURE_SUBSCRIPTION_ID	Azure Subscription ID
SONAR_TOKEN	SonarQube authentication token
SONAR_HOST_URL	SonarQube server URL
SNYK_TOKEN	Snyk authentication token
▶️ How to Run

Fork or clone this repo.

Add GitHub secrets listed above.

Push changes to the testing branch → triggers CI pipeline.

Merge into main → triggers production deployment.

Optionally, trigger staging deployment manually for acceptance testing.
