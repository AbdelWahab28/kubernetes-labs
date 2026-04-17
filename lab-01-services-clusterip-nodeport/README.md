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

---

## 🔧 Prérequis

-Docker
-Minikube
-kubectl
-Navigateur web

---

## 📁 Structure du lab

```bash
lab-01-services-clusterip-nodeport/
├── Dockerfile
├── frontend/           # code de l'application React
├── deployment.yaml     # Deployment pour Kubernetes
├── service_clusterip.yaml  # Service interne ClusterIP
├── service_nodeport.yaml   # Service externe NodePort
└── README.md
```
## Déploiement et exécution
Vérification :
```bash
docker --version
minikube version
kubectl version --client
```
▶️ Démarrage du cluster Minikube
```bash
minikube start
kubectl get nodes
```
🐳 Construction de l’image Docker
```bash
eval $(minikube docker-env)
docker build -t react-frontend:1.0 .
docker images
```
1️⃣ Deployment
```bash
kubectl apply -f deployment.yaml
kubectl get pods
```
2️⃣ Service ClusterIP
```bash
kubectl apply -f service_clusterip.yaml
kubectl get svc
```
3️⃣ Service NodePort
```bash
kubectl apply -f service_nodeport.yaml
kubectl get svc
```

## 🧹 Nettoyage du lab
```bash
kubectl delete -f service_nodeport.yaml
kubectl delete -f service_clusterip.yaml
kubectl delete -f deployment.yaml
minikube stop
```
<img width="608" height="393" alt="acceuil" src="https://github.com/user-attachments/assets/a8349ae4-e69f-43d0-989d-a14462e2f8f9" />

<img width="612" height="108" alt="2" src="https://github.com/user-attachments/assets/373f242e-a892-4315-b31f-6e2bc068a324" />

<img width="609" height="170" alt="4" src="https://github.com/user-attachments/assets/3a3064f0-79e4-46ea-84c4-da773b022a68" />

<img width="607" height="172" alt="5" src="https://github.com/user-attachments/assets/5100df55-b76a-48af-9337-894d427d8967" />

<img width="604" height="123" alt="7" src="https://github.com/user-attachments/assets/7fe07270-fd76-4476-b5dd-8c92e48f4cf4" />

## 📄 Documentation détaillée

La documentation complète du projet (explications, captures d’écran...)
est disponible sur mon LinkedIn : https://linkedin.com/in/abdelwahab28
