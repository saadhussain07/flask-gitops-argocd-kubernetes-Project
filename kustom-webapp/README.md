# 🧩 ArgoCD + Kustomize Deployment

This module demonstrates deploying applications using **Kustomize with ArgoCD**.

---

## 📌 Overview

Kustomize allows you to customize Kubernetes YAML configurations without modifying the original files.

---

## 📁 Structure

```
kustomize-app/
├── base/
└── overlays/
    ├── dev/
    └── prod/
```

---

## ⚙️ Deployment via ArgoCD

```bash
argocd app create kustomize-app \
--repo <your-repo-url> \
--path kustomize-app/overlays/prod \
--dest-server https://kubernetes.default.svc \
--dest-namespace prod
```

---

## 🔄 How It Works

* **Base** → Common configuration
* **Overlays** → Environment-specific changes

---

## 🌍 Environments

| Environment | Purpose    |
| ----------- | ---------- |
| dev         | Testing    |
| prod        | Production |

---

## ✅ Key Benefits of Kustomize

* No templating language
* Native Kubernetes integration
* Clean separation of environments

---

## 🧠 Use Case

Best suited for:

* Environment-specific deployments
* Simpler YAML customization
* GitOps workflows
