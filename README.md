# 🚀 MERN ThinkBoard – Complete DevOps Pipeline on Kubernetes

This project demonstrates a **production-grade DevOps pipeline** for a MERN application, covering the full lifecycle from source code to deployment and observability on Kubernetes, fully automated using modern DevOps tools.

It is designed as a **portfolio-ready project** to showcase real-world DevOps skills including CI/CD, GitOps, containerization, Kubernetes, and monitoring.

---

## 🧠 Project Overview

The goal of this project is to:

- Automate application build and Docker image creation
- Push images securely to Docker Hub
- Apply GitOps principles using Argo CD
- Deploy the application to a Kubernetes cluster
- Monitor the cluster and application using Prometheus & Grafana
- Run everything on cloud infrastructure (AWS)

---

## 🏗️ Architecture Diagram

📌 **Path:**


**Description:**  
This diagram illustrates the full DevOps workflow, from GitHub commits to Kubernetes deployment and monitoring.

---

## 🧰 Tech Stack

### Application
- Frontend: React
- Backend: Node.js (Express)
- Database: MongoDB

### DevOps & Cloud
- CI/CD: Jenkins
- Containerization: Docker
- Container Registry: Docker Hub
- Orchestration: Kubernetes (kubeadm on EC2)
- GitOps: Argo CD
- Monitoring: Prometheus & Grafana
- Cloud Provider: AWS (EC2)

---

## 📂 Repositories Structure

### 🔹 Application Repository
📎 https://github.com/salemgaleb3-devops/mern-thinkboard.git

Contains:
- MERN application source code
- Backend Dockerfile
- Application logic

---

### 🔹 Kubernetes Manifests Repository (GitOps)
📎 https://github.com/salemgaleb3-devops/k8s-yaml-mern-thinkboard.git

Contains:
- Kubernetes manifests
- Deployment, Service, Ingress
- Monitoring configuration

---

## 🔄 CI/CD Pipeline Workflow

### 1️⃣ Code Commit (GitHub)

Developer pushes code to the `mern-thinkboard` repository.

📸 **Screenshot:**

---

### 2️⃣ Jenkins CI Pipeline

Jenkins performs the following automatically:

- Clones the application repository
- Builds Docker image from Dockerfile
- Pushes image to Docker Hub
- Triggers update in Kubernetes manifests repository

📸 **Jenkins Pipeline Screenshot**

---

### 3️⃣ Docker Image Build & Push

- Image built using a multi-layer Dockerfile
- Tagged and pushed to Docker Hub

📸 **Docker Hub Image Screenshot**

---

## ☸️ Kubernetes Deployment

- Application deployed as Kubernetes Deployment
- Services expose backend and frontend
- Ingress manages external access

📸 **Kubernetes Pods & Services**

---

## 📊 Monitoring & Observability

### 🔹 Prometheus

Scrapes metrics from:
- Kubernetes cluster
- Nodes

📸 **Prometheus Targets**

---

### 🔹 Grafana

Preconfigured dashboards for:
- Cluster health
- Node performance
- Application metrics (HTTP requests, latency, errors)

📸 **Grafana Dashboards**

---

## ☁️ Cloud Infrastructure (AWS)

- EC2 instances used for Kubernetes nodes
- kubeadm-based cluster
- All components run in the cloud

📸 **AWS EC2 Instances**

---

## 🔐 Security & Best Practices

- Secrets managed via Kubernetes Secrets
- GitOps ensures immutable deployments
- Separation of application code and infrastructure
- Automated CI/CD with minimal manual intervention

---

## 🎯 Key DevOps Concepts Demonstrated

✔ CI/CD automation  
✔ Docker image lifecycle  
✔ GitOps (Argo CD)  
✔ Kubernetes production patterns  
✔ Monitoring & observability  
✔ Cloud-native architecture  

---

## 👨‍💻 Author

**Salem Bamakhraam**  
DevOps Engineer  

GitHub: https://github.com/salemgaleb3-devops
