Tenant Management 

Overview
The Tenant Management is a microservices-based application designed to use modern frameworks, cloud-native tools, and third-party integrations to provide scalable, maintainable, and efficient backend services and frontend interfaces.

This project consists of multiple services including:

Django API: Provides RESTful APIs for tenant and property management.

FastAPI Worker: Handles asynchronous background jobs and integrations.

PostgreSQL: Relational database for persistent storage.

Redis: In-memory data store for caching and message brokering.

Flutter Frontend: Mobile application for tenant interactions.

M-Pesa Payment Gateway: Enables secure and seamless mobile money payment processing.

SMS Gateway: Supports SMS notifications and alerts to tenants and admins.

Infrastructure as Code (IaC) using Terraform and Kubernetes manifests.

Logging and Monitoring: Using ELK stack and Prometheus/Grafana.

Frameworks and Tools Used
Backend
Django REST Framework (DRF)

Serves as the main web API framework.

Handles authentication, data validation, and CRUD operations.

Modular and extensible for future growth.

FastAPI

High-performance asynchronous Python framework.

Used for background task processing and real-time operations.

Celery

Task queue for managing asynchronous jobs and scheduled tasks.

Integrated with Redis as the message broker.

Databases
PostgreSQL

Primary relational database.

Data persistence with support for transactions and complex queries.

Persistent volumes configured to ensure data durability in Kubernetes.

Redis

In-memory cache and broker for Celery tasks.

Improves application responsiveness and scalability.

Payment Integration
M-Pesa Payment Gateway

Integrated via Safaricom's Daraja API.

Supports initiating STK Push payment prompts to users’ mobile devices.

Payment status callbacks update tenant payment records automatically.

Enables seamless, real-time rent payment through mobile money.

Notification Integration
SMS Gateway

Integrated through a third-party SMS service provider.

Sends SMS notifications for payment confirmations, reminders, and alerts.

Supports two-way communication for user verification and support.

Frontend
Flutter

Cross-platform mobile UI toolkit.

Provides responsive and native-like user experience on iOS and Android.

Infrastructure
Docker & Docker Compose

Containerize all services for consistency and ease of deployment.

Local development and testing via docker-compose.

Kubernetes

Orchestration of containerized services in production.

Manages scaling, networking, and service discovery.

Terraform

Infrastructure as Code tool to provision cloud infrastructure.

Automates resource creation and environment setup.

Ingress Controller + TLS

Secure HTTPS access to APIs and frontend via Kubernetes ingress.

Letsencrypt or custom TLS certificates support.

Logging & Monitoring
ELK Stack (Elasticsearch, Logstash, Kibana)

Centralized logging for observability and debugging.

Prometheus & Grafana

Metrics collection and visualization.

Monitors application health and resource usage.

CI/CD Pipeline
GitHub Actions

Automates build, test, and deployment processes.

Builds Docker images and deploys them to Kubernetes clusters automatically on code pushes.

Functionality
Tenant Management

CRUD operations for tenants, leases, payments, and maintenance requests.

Tenant authentication and profile management.

Property Management

Register and manage properties.

Track occupancy, availability, and rent schedules.

Payment Processing

Tenants can pay rent using mobile money via the integrated M-Pesa payment gateway.

Payment requests trigger STK Push prompts on tenants’ phones.

Payment results are handled via asynchronous callbacks, updating the system in real time.

Notifications

SMS alerts for payment confirmation, due rent reminders, and system notifications.

Supports two-way SMS for communication between tenants and management.

Asynchronous Task Handling

Background jobs such as sending notifications, data sync, and reports handled by FastAPI worker with Celery.

Mobile App Interface

Tenants interact with the system using the Flutter mobile app.

Features include rent payment, maintenance request submission, and communication.

Infrastructure Automation

Use Terraform to provision infrastructure resources.

Kubernetes manages the lifecycle of application components.

Observability

Centralized logs and performance metrics available through dashboards.

Alerting for critical issues.

Demonstration of Modern Application Development Concepts
This project demonstrates key modern software development concepts and best practices:

Version Control

Entire codebase maintained on GitHub.

Branching strategies and pull requests enable collaborative development.

Continuous Integration / Continuous Deployment (CI/CD)

Automated testing, building, and deployment with GitHub Actions.

Ensures reliable and repeatable releases with minimal manual intervention.

Microservices Architecture

Application is split into loosely coupled services (Django API, FastAPI worker, etc.).

Facilitates independent scaling, maintenance, and development.

Containerization

Docker is used to package services for consistent environments.

Enables easy local development and seamless cloud deployment.

Infrastructure as Code (IaC)

Terraform manages provisioning of cloud resources.

Kubernetes manifests define deployment, services, and ingress, ensuring reproducible infrastructure.

Cloud-Native Design

Services run inside Kubernetes for high availability and scalability.

Uses cloud managed databases and storage solutions.

Third-Party Service Integration

Incorporates external APIs such as M-Pesa payment and SMS gateways to enhance system capabilities.

Setup and Installation
Local Development
Clone the repository.

Start services with Docker Compose:

bash
Copy
Edit
cd infra/docker
docker-compose up -d
Access APIs and frontend locally.

Use database clients to connect to PostgreSQL.

Production Deployment
Provision infrastructure with Terraform:

bash
Copy
Edit
cd infra/terraform
terraform init
terraform apply
Deploy Kubernetes manifests:

bash
Copy
Edit
kubectl apply -f infra/kubernetes/
Set up ingress and TLS for secure access.

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