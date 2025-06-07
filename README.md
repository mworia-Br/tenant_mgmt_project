# 🏘️ Tenant Management System

A microservices-based tenant and property management system demonstrating modern cloud-native application design, containerization, and CI/CD automation.

## 🔧 Stack Overview

| Layer                | Technology                                                                 |
|---------------------|------------------------------------------------------------------------------|
| Backend APIs         | Django REST Framework, FastAPI, Celery                                      |
| Database & Cache     | PostgreSQL (persistent), Redis (in-memory)                                  |
| Mobile Frontend      | Flutter (cross-platform for Android & iOS)                                  |
| Asynchronous Tasks   | Celery + Redis                                                              |
| Payments             | M-Pesa via Safaricom Daraja API (STK Push & Callback)                       |
| Notifications        | SMS Gateway Integration (3rd-party API)                                     |
| Containerization     | Docker, Docker Compose                                                      |
| Orchestration        | Kubernetes + Ingress + TLS (Let's Encrypt or custom certs)                  |
| Infrastructure as Code | Terraform + K8s Manifests                                                  |
| CI/CD                | GitHub Actions (build, test, deploy)                                        |
| Logging & Monitoring | ELK Stack (Elastic, Logstash, Kibana), Prometheus & Grafana                 |

---

## 📦 Microservices

- **Django API**: Manages tenants, properties, leases, and payments.
- **FastAPI Worker**: Processes async jobs such as M-Pesa callbacks and SMS notifications.
- **Flutter Mobile App**: Enables tenants to interact with the system.
- **PostgreSQL**: Relational DB for persistent data.
- **Redis**: Caching and task brokering.

---

## 💰 Payment & SMS Integration

- **M-Pesa (Daraja API)**:
  - STK Push requests to tenant phones.
  - Callback updates payment records.
- **SMS Gateway**:
  - Sends rent reminders, confirmations, and alerts.
  - Supports two-way communication.

---

## 🚀 CI/CD Pipeline

- Automated with **GitHub Actions**:
  - Code push triggers Docker image builds.
  - Deployed to Kubernetes using manifests.
  - Secrets managed via GitHub and Kubernetes secrets.

---

## 🔐 Infrastructure

- **Terraform** provisions cloud infrastructure (VMs, buckets, DB).
- **Kubernetes** manages service deployment, scaling, and networking.
- **Ingress + TLS** provides secure HTTPS access.

---

## 🧪 Features Demonstrated

- ✅ Version control with Git + GitHub.
- ✅ CI/CD automation.
- ✅ Microservices with Python + Flutter.
- ✅ Containerization with Docker.
- ✅ Infrastructure as Code.
- ✅ Real-world integrations (M-Pesa + SMS).
- ✅ Observability via centralized logging & monitoring.

---

## 🛠️ Local Development

```bash
git clone https://github.com/mworia-Br/tenant-mgmt.git
cd infra/docker
docker-compose up -d


CI/CD Pipeline
Push code to main branch triggers build, test, and deployment.

Docker images are pushed to the container registry.

Kubernetes cluster updates deployed services automatically.

Troubleshooting
Docker issues: Ensure Docker daemon is running and you have enough resources.

Kubernetes errors: Check context with kubectl config current-context, verify cluster accessibility.

Database persistence: Confirm PVCs are bound and volumes mounted properly.

Ingress/TLS problems: Verify ingress controller is installed and certificates are valid.

Payment gateway errors: Check API credentials and webhook endpoint accessibility.

SMS delivery failures: Confirm SMS gateway credentials and network connectivity.

CI/CD failures: Check GitHub Action logs for errors in build or deployment steps.

Contributing
Feel free to open issues or pull requests to improve the project. Follow coding guidelines and document changes clearly.

License
This project is licensed under the MIT License.
