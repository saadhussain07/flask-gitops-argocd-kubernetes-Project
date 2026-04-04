# 🚢 ArgoCD + Helm Deployment

This module demonstrates how to deploy an application using **Helm charts managed by ArgoCD**.

---

## 📌 Overview

Helm is a package manager for Kubernetes that simplifies application deployment using reusable templates.

In this project:

* Helm charts define Kubernetes resources
* ArgoCD manages deployment via GitOps
* Configuration is controlled through `values.yaml`

---

## 📁 Structure

```
helm-app/
├── charts/
├── values.yaml
└── templates/
```

---

## ⚙️ Deployment via ArgoCD

ArgoCD pulls the Helm chart from the repository and deploys it automatically.

### Example Command:

```bash
argocd app create helm-app \
--repo <your-repo-url> \
--path helm-app \
--dest-server https://kubernetes.default.svc \
--dest-namespace default
```

---

## 🔧 Customization

Modify deployment behavior via:

* `values.yaml`
* Environment-specific overrides

---

## ✅ Key Benefits of Helm

* Reusable templates
* Parameterized configurations
* Easy upgrades & rollbacks

---

## 🧠 Use Case

Best suited for:

* Complex applications
* Reusable deployments
* Standardized environments
