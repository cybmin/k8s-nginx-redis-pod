# Multi-Container Pod with NGINX & Redis on Kubernetes (Using Colima)

This project demonstrates how to deploy a **multi-container pod** on Kubernetes using **Colima** as the container runtime. The pod runs:
- An **NGINX** web server
- A **Redis** in-memory data store

These containers share the same pod and can communicate internally over `localhost`.

---

## 🚀 What You Learn

- How to run Kubernetes locally using **Colima** (lightweight alternative to Docker Desktop)
- How to create and deploy multi-container pods
- Basics of Kubernetes `kubectl` usage
- Logging from multiple containers in a single pod
- GitHub workflow for DevOps/Cloud portfolios

---

## 🔧 Tools Used

- **Colima**: Container runtime with Kubernetes support (https://github.com/abiosoft/colima)
- **kubectl**: Kubernetes CLI
- **NGINX**: Web server
- **Redis**: In-memory database
- **Git** + **GitHub**

---

## 📦 Deployment Steps

### ✅ Prerequisites

Make sure these are installed:
- [Colima](https://github.com/abiosoft/colima)  
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)  
- Git

---

### 🧱 Start Kubernetes with Colima

```bash
colima start --with-kubernetes


📄 Create the multi-container pod
multi-container-pod.yaml:

yaml
Copy
Edit
apiVersion: v1
kind: Pod
metadata:
  name: nginx-redis-pod
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
    - name: redis
      image: redis
      ports:
        - containerPort: 6379
Apply it:

bash
Copy
Edit
kubectl apply -f multi-container-pod.yaml

🔍 Check Status & Logs
kubectl get pods
kubectl describe pod nginx-redis-pod
kubectl logs nginx-redis-pod -c nginx
kubectl logs nginx-redis-pod -c redis

🚀 Push to GitHub
bash
git init
git add .
git commit -m "Multi-container pod using NGINX and Redis with Colima"
git remote add origin https://github.com/cybmin/k8s-nginx-redis-pod.git
git branch -M main
git push -u origin main
