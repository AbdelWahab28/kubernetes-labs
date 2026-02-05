# Lab 01 – Services Kubernetes : ClusterIP & NodePort

Ce lab illustre le déploiement d’une **application React** sur un **cluster Kubernetes Minikube** avec l’exposition via **Service ClusterIP** et **NodePort**.

L’objectif est de comprendre comment Kubernetes gère les pods, les services internes et l’accès externe.

---

## 🎯 Objectifs du lab

- Déployer une application conteneurisée dans Kubernetes
- Créer un **Deployment** pour gérer les pods
- Exposer l’application avec un **Service ClusterIP**
- Exposer l’application vers l’extérieur avec un **Service NodePort**
- Vérifier l’accessibilité via Minikube ou navigateur

---

## 🛠️ Technologies utilisées

- Kubernetes (Minikube)
- Docker (pour construire l’image React)
- React
- Node.js
- Git / GitHub
- Linux / Windows (Minikube compatible)

---

## 📁 Structure du lab

```bash
lab-01-services-clusterip-nodeport/
├── Dockerfile
├── frontend/           # code de l'application React
├── deployment.yaml     # Deployment pour Kubernetes
├── service-clusterip.yaml  # Service interne ClusterIP
├── service-nodeport.yaml   # Service externe NodePort
└── README.md
