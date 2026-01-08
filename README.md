# 🚀 DevOps Tasks – Node.js Docker & Kubernetes

This repository demonstrates a complete DevOps workflow using a simple Node.js application, covering Git, Docker, Docker Hub, and Kubernetes from scratch.

---

## 📌 Project Overview

The purpose of this project is to:

- Create a Node.js application
- Containerize the application using Docker
- Push the Docker image to Docker Hub
- Deploy the application to Kubernetes using Deployment and Service
- Debug and fix real-world issues (CrashLoopBackOff)
- Validate the application using port-forwarding

This project is designed for learning, practice, and interview preparation.

---

## 🧠 High-Level Workflow

Code
→ Git (branch, commit, push)
→ Dockerfile
→ Docker Image (local)
→ Docker Hub Image (remote)
→ Kubernetes Deployment
→ Pod
→ Service
→ Port Forward
→ Browser / curl

yaml
Copy code

---

## 📁 Repository Structure

Devops-Tasks/
├── Dockerfile
├── .dockerignore
├── README.md
├── package.json
├── server.js
└── k8s/
├── deployment.yaml
└── service.yaml

yaml
Copy code

---

## 🛠️ Tech Stack

- Node.js
- Git & GitHub
- Docker
- Docker Hub
- Kubernetes (Minikube)

---

## 🐳 Docker

### Build Docker Image

```bash
docker build -t node-hello:1.0 .
Run Container Locally
bash
Copy code
docker run -p 3000:3000 node-hello:1.0
Expected response:

nginx
Copy code
Hello World!
📦 Docker Hub
Tag Image
bash
Copy code
docker tag node-hello:1.0 rootdp1703/node-app:1.0
Push Image
bash
Copy code
docker push rootdp1703/node-app:1.0
Kubernetes pulls images from Docker Hub, not from the local machine.

☸️ Kubernetes Deployment
Apply Kubernetes manifests:

bash
Copy code
kubectl apply -f k8s/
Verify resources:

bash
Copy code
kubectl get deployments
kubectl get pods
kubectl get svc
🌐 Access Application (Port Forward)
bash
Copy code
kubectl port-forward svc/node-hello-svc 8080:80
Test:

bash
Copy code
curl http://localhost:8080
Expected response:

nginx
Copy code
Hello World!
🐞 Debugging CrashLoopBackOff
Debugging steps used in this project:

bash
Copy code
kubectl get pods
kubectl logs <pod-name>
kubectl describe pod <pod-name>
docker run <image>
Root Cause
Dockerfile entrypoint was incorrect

Application file path did not exist inside the container

Dockerfile was fixed

Image rebuilt and pushed

Kubernetes rollout succeeded

🔄 Rolling Updates
New pods were created during deployment updates

Old pods were terminated only after new pods became ready

Zero downtime was maintained

📘 Key Learnings
Dockerfile builds Docker images

Docker images can have multiple tags

Docker Hub stores images, not Dockerfiles

Kubernetes cannot access local images

CrashLoopBackOff usually indicates application startup issues

🎯 Future Enhancements
Liveness and Readiness Probes

Ingress and Load Balancer

ConfigMaps and Secrets

Horizontal Pod Autoscaler (HPA)

CI/CD using GitHub Actions

👨‍💻 Author
Dhruv Patel
Learning DevOps through hands-on practice 🚀

yaml
Copy code

---

### ✅ How to Use

1. Open `README.md` in your repo  
2. **Select all → Paste**  
3. Commit and push

```bash
git add README.md
git commit -m "Add project README"
git push
