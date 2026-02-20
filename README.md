App Link: https://healthify-me-app.streamlit.app/

# HealthifyMe – GitOps-based Kubernetes Deployment 🚀

HealthifyMe is a containerized AI-powered wellness application deployed on Kubernetes using a modern **GitOps CI/CD pipeline**.  
The project demonstrates best practices using **Docker, GitHub Actions, Helm, and Argo CD** for automated builds, declarative deployments, and continuous delivery.

---

## 🏗️ Architecture Overview

The deployment follows a GitOps model where **GitHub is the single source of truth**, and Argo CD continuously reconciles the desired state into Kubernetes.

**Pipeline Flow:**

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/14d3cb83-19bf-48dc-8073-140fb132d4d8" />

---

## 🧰 Tech Stack

- **Application**: Python (Streamlit)
- **Containerization**: Docker
- **CI**: GitHub Actions
- **Image Registry**: Docker Hub
- **CD / GitOps**: Argo CD
- **Packaging**: Helm
- **Orchestration**: Kubernetes (Minikube)
- **Secrets Management**: Kubernetes Secrets


---

## 🔄 CI Pipeline (GitHub Actions)

Triggered on every push to the `main` branch.

### CI Responsibilities:
- Checkout source code
- Build Docker image
- Push image to Docker Hub

> CI **does not deploy** to Kubernetes. Deployment is handled via GitOps using Argo CD.

---

## 🚢 CD Pipeline (Argo CD – GitOps)

Argo CD continuously:
- Monitors the GitHub repository
- Compares Git state with Kubernetes state
- Automatically syncs changes using Helm charts

### Key Features:
- Automated sync
- Drift detection & self-healing
- Declarative rollback via Git

---

## ⚙️ Helm Configuration

Image and runtime configuration are managed via `values.yaml`:

image:
  repository: rahulbohra57/healthifyme-app
  tag: v1

service:
  type: NodePort
  port: 8501

Updating values.yaml triggers an automatic deployment via Argo CD.

--

🔁 Rollbacks & Reliability

- Rollbacks are performed by updating Git (values.yaml)
- Argo CD reconciles the rollback automatically
- No manual intervention required in Kubernetes

--

🎯 Key Learnings

- Git as the single source of truth
- Safe deployments with GitOps
- Declarative rollback strategy
- CI/CD separation of concerns
- Real-world Kubernetes troubleshooting
