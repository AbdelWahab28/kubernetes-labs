# Lab 03 – Kubernetes Secrets & ConfigMaps

## 🧠 Objectif
Ce projet a pour but de comprendre la gestion des configurations et des données sensibles dans Kubernetes à travers les ConfigMaps et les Secrets.

Il démontre :
- Comment externaliser la configuration d’une application
- Comment sécuriser les informations sensibles (mot de passe, variables d’environnement…)
- Comment injecter ces données dans un Pod

---

## 🛠️ Technologies utilisées
- Kubernetes (Minikube)
- ConfigMap
- Secret
- Deployment
- Variables d’environnement
- Application Laravel-Mysql

---

## 📁 Structure du lab
```bash
lab-03-secrets-configmaps/
│
├─ Laravel/
│  ├─ Dockerfile              # Dockerfile Laravel
│  └─ .dockerignore
│  └─ App                     # Dossier application
│
├─ manifestk8s/
│  ├─ configmap.yaml          # ConfigMap Laravel
│  ├─ secret.yaml             # Secrets MySQL + Laravel
│  ├─ mysql-pvc.yaml          # PersistentVolumeClaim MySQL
│  ├─ mysql-deployment.yaml   # Deployment + Service MySQL
│  ├─ laravel-deployment.yaml # Deployment + Service Laravel
│
└─ README.md
```
## Déploiement et exécution

1️⃣ Démarrage du cluster Minikube
```bash
minikube start
kubectl get nodes
```
2️⃣ Build image Laravel
```bash
eval $(minikube docker-env)
docker build -t backend-laravel /Laravel .
```
3️⃣ Appliquer la config
```bash
kubectl apply -f manifestk8s/configmap.yaml
kubectl apply -f manifestk8s/secret.yaml
```
4️⃣ Créer le StorageClass 
```bash
kubectl apply -f manifestk8s/mysql-pvc.yaml
```
5️⃣ DB et APP
```bash
kubectl apply -f manifestK8s/mysql-deployment.yaml
kubectl apply -f manifestk8s/laravel-deployment.yaml
```

## 🧹 Nettoyage du lab
```bash
kubectl delete -f laravel-deployment.yaml
kubectl delete -f mysql-deployment.yaml
kubectl delete -f mysql-pvc.yaml
minikube stop
```
<img width="1089" height="527" alt="1" src="https://github.com/user-attachments/assets/a3a859f8-edb9-40c9-97b0-48aaf31fc3fe" />

## 📄 Documentation détaillée

La documentation complète du projet (explications, captures d’écran...)
est disponible sur mon LinkedIn : https://www.linkedin.com/in/abdourahamaneabdelwahab
