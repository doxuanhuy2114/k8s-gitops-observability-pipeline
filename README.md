# ?? Production-Grade Local K8s Cluster & GitOps Observability Pipeline

[![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.27-blue?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![ArgoCD](https://img.shields.io/badge/GitOps-ArgoCD-orange?style=for-the-badge&logo=argo&logoColor=white)](https://argoproj.github.io/cd/)
[![Prometheus](https://img.shields.io/badge/Monitoring-Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Dashboard-Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)](https://grafana.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

A complete production-grade DevOps repository showcasing end-to-end Kubernetes cluster provisioning, full-stack observability, and automated GitOps Continuous Delivery.

---

System Architecture


               +-------------------------------------------------+
               |             Kind Kubernetes Cluster             |
               |                                                 |
+----------+   |  +------------------+   +--------------------+  |
|  Git     |   |  |   Control Plane  |   |    Worker Node 1   |  |
|          |   |  +------------------+   +--------------------+  |
| Repos    |--->  |  ArgoCD Engine   |   |  Guestbook App Pod |  |
+----------+   |  +------------------+   +--------------------+  |
               |                         |    Worker Node 2   |  |
               |                         +--------------------+  |
               |                         | Prometheus/Grafana |  |
               |                         +--------------------+  |
               +-------------------------------------------------+

---

Tech Stack & Key Components

**Infrastructure Orchestration:** Kubernetes (Kind), WSL2, Docker Desktop.
**Continuous Delivery (GitOps):** ArgoCD with \Auto-Sync\, \Prune\, and \Self-Heal\ policies.
**Observability & Monitoring:** \kube-prometheus-stack\ via Helm, Grafana Real-time Dashboards.
**Automation & CI:** GitHub Actions (YAML Syntax Validation & Linting).

---

Proof of Concept & Visual Evidence

1. Multi-Node Cluster Status (\kubectl get nodes\)

<img width="975" height="511" alt="image" src="https://github.com/user-attachments/assets/ecd3d6f1-0a2d-4234-a4c5-56aed8301840" />


2. Real-time Cluster Metrics & Resource Monitoring (Grafana)

<img width="975" height="496" alt="image" src="https://github.com/user-attachments/assets/1f1fb6ba-cdcb-4d83-a967-fe7b09db765e" />
<img width="975" height="498" alt="image" src="https://github.com/user-attachments/assets/97375e4b-3a80-43fd-a50e-50a79397a768" />
<img width="975" height="494" alt="image" src="https://github.com/user-attachments/assets/f50aa0c1-cac6-4457-ba15-c75a5d3bc12e" />
<img width="975" height="498" alt="image" src="https://github.com/user-attachments/assets/4f4f0b8b-a279-4b75-ac4a-f7bee0e1f1b0" />

3. ArgoCD GitOps Engine Control Plane

<img width="975" height="498" alt="image" src="https://github.com/user-attachments/assets/23588f35-bce6-4933-9eb3-53a641ac5529" />
<img width="975" height="496" alt="image" src="https://github.com/user-attachments/assets/ec5400b1-862e-43fd-ab82-1939544441cf" />

4. Application Topology & Continuous Synchronization Status

<img width="975" height="497" alt="image" src="https://github.com/user-attachments/assets/a7ae0aa2-a554-42ec-a616-621c299ab9b4" />
<img width="975" height="497" alt="image" src="https://github.com/user-attachments/assets/61ef5aa1-d61a-4e0c-afbf-c0ac0698dc21" />

---

Quickstart Guide

1. Provision Cluster
\\\
Bash
  kind create cluster --name devops-cluster --config kind-config.yaml
\\\

2. Install Monitoring Stack
\\\
Bash
  helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
  helm repo update
  helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring --create-namespace
\\\

3. Install ArgoCD
\\\
Bash
  kubectl create namespace argocd
  kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
\\\

---
*Maintained by **Huy Do ([@doxuanhuy2114](https://github.com/doxuanhuy2114))***
