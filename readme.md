# 🚀 ArgoCD Deployment Guide (Beginner → Pro)

Welcome to this hands-on project where you’ll learn how to **install, configure, and manage applications using ArgoCD** in Kubernetes.

This guide is designed to be simple, practical, and easy to follow — whether you're just starting or brushing up your DevOps skills.

---

## 📌 Overview

This project demonstrates:

* Installing **ArgoCD** on Kubernetes
* Accessing the ArgoCD UI
* Authenticating via CLI
* Creating and managing applications
* Using essential ArgoCD commands

---

## 🎥 Learning Resource

Follow this video for a complete walkthrough:

👉 https://youtu.be/JLrR9RV9AFA

---

## ⚙️ Installation Guide

### 1️⃣ Create Namespace & Install ArgoCD

```bash
kubectl create namespace argocd

kubectl apply -n argocd \
-f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

---

### 2️⃣ Access ArgoCD Server (Port Forwarding)

```bash
kubectl get services -n argocd

kubectl port-forward service/argocd-server -n argocd 8080:443
```

👉 Access UI: https://localhost:8080

---

### 3️⃣ Retrieve Admin Credentials

```bash
kubectl -n argocd get secret argocd-initial-admin-secret \
-o jsonpath="{.data.password}" | base64 -d
```

* **Username:** `admin`
* **Password:** (output from above command)

---

## 💻 ArgoCD CLI Setup

### Install CLI

```bash
brew install argocd
```

> 💡 For Linux/Windows, download from official releases.

---

### Login via CLI

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443

argocd login 127.0.0.1:8080
```

---

## 📦 Create an Application

Deploy an app using ArgoCD CLI:

```bash
argocd app create webapp-kustom-prod \
--repo https://github.com/devopsjourney1/argo-examples.git \
--path kustom-webapp/overlays/prod \
--dest-server https://kubernetes.default.svc \
--dest-namespace prod
```

---

## 🧰 ArgoCD Command Cheat Sheet

| Command                     | Description              |
| --------------------------- | ------------------------ |
| `argocd app create`         | Create a new application |
| `argocd app list`           | List all applications    |
| `argocd app get <app>`      | Get app details          |
| `argocd app logs <app>`     | View logs                |
| `argocd app diff <app>`     | Compare with Git         |
| `argocd app sync <app>`     | Sync app with repo       |
| `argocd app history <app>`  | View deployment history  |
| `argocd app rollback <app>` | Rollback changes         |
| `argocd app set <app>`      | Update configuration     |
| `argocd app delete <app>`   | Delete application       |

---

## 🧠 Key Concepts

* **GitOps**: Your Git repo is the source of truth
* **Declarative Deployments**: Define desired state, ArgoCD enforces it
* **Continuous Delivery**: Automated syncing of changes

---

## 📁 Project Purpose

This project was built to:

* Practice real-world DevOps workflows
* Understand ArgoCD architecture
* Learn Kubernetes application deployment

---

## ⭐ Tips

* Always keep your manifests version-controlled
* Use namespaces for isolation
* Monitor sync status regularly

---

## 🤝 Contributing

Feel free to fork, improve, and submit pull requests!

---

## 📜 License

This project is open-source and available under the MIT License.

---

### 💡 Final Note

This is a beginner-friendly setup — once you're comfortable, explore:

* Helm integrations
* Multi-cluster setups
* Automated sync policies

---

🚀 Happy Deploying with ArgoCD!
