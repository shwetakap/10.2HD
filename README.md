# 🚀 DevOps Project: Automated CI/CD Pipeline with Azure AKS

This project demonstrates a full **DevOps CI/CD pipeline** implementation for a containerized application using **GitHub Actions, Docker, Terraform, SonarCloud, Snyk, and Azure Kubernetes Service (AKS)**.  

It covers the complete lifecycle:  
- Continuous Integration (**Build, Test, Scan, Push**)  
- Continuous Deployment (**Staging → Production**)  
- Infrastructure as Code with **Terraform**  


---

## 📌 Features Implemented

1. **Continuous Integration (CI)**
   - Automated build of Docker images.
   - Unit testing with `pytest`.
   - Code quality analysis with **SonarCloud**.
   - Security vulnerability scanning with **Snyk** and **Grype/Syft**.
   - Push built images to **Azure Container Registry (ACR)**.

2. **Staging Deployment**
   - Infrastructure provisioning with **Terraform** on Azure.
   - Deployment of application to **staging AKS environment**.
   - Postman API tests to validate functionality.
   - Automated cleanup (`terraform destroy`) after pipeline completion.

3. **Production Deployment**
   - Manual approval step before production release.
   - Deployment of application to **production AKS** using `docker-compose.prod.yml`.
   


---

## ⚙️ Tech Stack

- **Languages/Frameworks**: Python, Node.js (MERN)
- **CI/CD**: GitHub Actions
- **Containerization**: Docker, Docker Compose
- **Infrastructure**: Terraform (Azure AKS + ACR)
- **Testing**: Pytest, Postman (integration tests)
- **Code Quality & Security**: SonarCloud, Snyk, Grype, Syft
- **Secrets Management**: GitHub Secrets

---

## 🔑 GitHub Secrets Required

Add these secrets in your GitHub repository settings:

| Secret Name            | Purpose                                         |
|-------------------------|-------------------------------------------------|
| `AZURE_CREDENTIALS`    | Service principal JSON for Terraform + AKS auth |
| `ACR_NAME`             | Azure Container Registry name                   |
| `SONAR_TOKEN`          | Authentication token for SonarCloud             |
| `SONAR_HOST_URL`       | SonarCloud instance URL (e.g., `https://sonarcloud.io`) |
| `SNYK_TOKEN`           | Token for Snyk security scans                   |

---

## 📂 Project Structure

```bash
.
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
├── postman
└── README.md
