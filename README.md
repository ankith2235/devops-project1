# DevOps Capstone Project – End-to-End CI/CD Lifecycle

This project demonstrates the implementation of a complete DevOps lifecycle for a production-based web application at Analytics Pvt. Ltd. The company needed a scalable and automated deployment pipeline to handle increasing user demand without modifying the original Docker setup used in testing.

---

## 🏢 Project Background

Analytics Pvt. Ltd. runs a monolithic web application hosted in a GitHub repository:  
👉 https://github.com/hshar/website.git

With rapid user growth, the company required automation of:
- Deployment  
- Scaling  
- Container orchestration  
- Infrastructure provisioning  

This capstone project builds a **full CI/CD pipeline** using AWS, Jenkins, Docker, Kubernetes, CodeBuild, Terraform, and Ansible.

---

## 🚀 DevOps Lifecycle Requirements

### ✔️ Git Strategy & Version Control
- Implemented Git workflow suitable for monolithic architecture
- Managed releases — **deployment is triggered only on the 25th of every month**
- Tracked code commits and automated build triggers

---

### ✔️ AWS CodeBuild Automation
- CodeBuild job configured to start **when commits are pushed to the `master` branch**
- CodeBuild pulls updated code from GitHub automatically

---

### ✔️ Docker Image Build & Push
- Created custom Dockerfile
- Container image built every time there is a push to GitHub
- Docker image pushed to **Docker Hub**
- Maintained Docker versioning for production use

---

### ✔️ Kubernetes Deployment (Production)
- Deployed containerized application to Kubernetes cluster
- Used **2 replicas** for high availability
- Created a **NodePort service** exposed at **30008**
- Supports scaling and zero-downtime rollout

---

### ✔️ Jenkins CI/CD Pipeline
- End-to-end Jenkins Pipeline script created to:
  1. Pull code from GitHub
  2. Trigger CodeBuild
  3. Build Docker image & push to Docker Hub
  4. Deploy container on Kubernetes cluster
  5. Run rollout status validation

- Single pipeline automates build → test → deploy

---

### ✔️ Configuration Management (Ansible)
- Used Ansible to install and configure software on 4 worker servers

| Worker Node | Installed Software |
|-------------|-------------------|
| Worker 1    | Jenkins, Java     |
| Worker 2    | Docker, Kubernetes |
| Worker 3    | Java, Docker, Kubernetes |
| Worker 4    | Docker, Kubernetes |

Ansible ensures all infrastructure nodes are consistently configured.

---

### ✔️ Terraform Infrastructure Provisioning
- Provisioned AWS compute resources using Terraform
- Automated creation of required instances
- Output variables used for Jenkins and Ansible inventory
- Infrastructure is reusable, repeatable, and version-controlled

---

## 🧰 Tools & Technologies Used
- Git & GitHub
- AWS CodeBuild
- Terraform (IaC)
- Jenkins Pipeline
- Docker & Docker Hub
- Kubernetes (NodePort Service – port 30008)
- Ansible (Configuration Management)
- Linux (Ubuntu)

---

## 🏁 End-to-End Workflow

1️⃣ Developer pushes code → **master** branch  
2️⃣ GitHub triggers CodeBuild  
3️⃣ CodeBuild starts Jenkins pipeline  
4️⃣ Pipeline builds Docker image → pushes to Docker Hub  
5️⃣ Kubernetes pulls image → starts **2 replicas**  
6️⃣ Service is exposed at **NodePort: 30008**  
7️⃣ Terraform + Ansible ensure infrastructure is configured & repeatable

---

## 🎯 Business Impact
- Eliminated manual deployments
- Reduced release errors
- Achieved auto-scaling and container orchestration
- Standardized environment setup with IaC + CM
- Enabled predictable monthly release cycles

---

## 📌 Summary
This capstone project integrates **every major DevOps component** into a single working solution:
- Infrastructure (Terraform)
- Configuration (Ansible)
- CI/CD (Jenkins + CodeBuild)
- Containers (Docker)
- Orchestration (Kubernetes)
- Version control & workflow (Git)

It demonstrates full-stack DevOps implementation from source control to production deployment.

