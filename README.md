# ?? Production-Grade Local K8s Cluster & GitOps Observability Pipeline

[![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.27-blue?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![ArgoCD](https://img.shields.io/badge/GitOps-ArgoCD-orange?style=for-the-badge&logo=argo&logoColor=white)](https://argoproj.github.io/cd/)
[![Prometheus](https://img.shields.io/badge/Monitoring-Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Dashboard-Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)](https://grafana.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

A complete production-grade DevOps repository showcasing end-to-end Kubernetes cluster provisioning, full-stack observability, and automated GitOps Continuous Delivery.

---

## ?? System Architecture

\\\	ext
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
\\\

---

## ??? Tech Stack & Key Components

* **Infrastructure Orchestration:** Kubernetes (Kind), WSL2, Docker Desktop.
* **Continuous Delivery (GitOps):** ArgoCD with \Auto-Sync\, \Prune\, and \Self-Heal\ policies.
* **Observability & Monitoring:** \kube-prometheus-stack\ via Helm, Grafana Real-time Dashboards.
* **Automation & CI:** GitHub Actions (YAML Syntax Validation & Linting).

---

## ?? Proof of Concept & Visual Evidence

### 1. Multi-Node Cluster Status (\kubectl get nodes\)
![K8s Nodes](docs/images/01-cluster-nodes.png)

### 2. Real-time Cluster Metrics & Resource Monitoring (Grafana)
![Grafana Dashboard](docs/images/02-grafana-metrics.png)

### 3. ArgoCD GitOps Engine Control Plane
![ArgoCD Dashboard](docs/images/03-argocd-ui.png)

### 4. Application Topology & Continuous Synchronization Status
![ArgoCD App Topology](docs/images/04-argocd-topology.png)

---

## ? Quickstart Guide

### 1. Provision Cluster
\\\ash
kind create cluster --name devops-cluster --config kind-config.yaml
\\\

### 2. Install Monitoring Stack
\\\ash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring --create-namespace
\\\

### 3. Install ArgoCD
\\\ash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
\\\

---
*Maintained by **Huy Do ([@doxuanhuy2114](https://github.com/doxuanhuy2114))***
