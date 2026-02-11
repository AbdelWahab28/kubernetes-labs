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

<img width="1542" height="726" alt="2" src="https://github.com/user-attachments/assets/ba3a10df-3715-4f49-9c54-11e9dd688b52" />

<img width="1318" height="530" alt="7" src="https://github.com/user-attachments/assets/e1bf36bf-6a32-4852-a26f-9229b3a24f61" />

<img width="1176" height="810" alt="8" src="https://github.com/user-attachments/assets/a42f809f-64d7-4e14-a556-af7af3dc56b5" />

<img width="1710" height="966" alt="11" src="https://github.com/user-attachments/assets/db4d7b7a-ba3e-405c-8f8d-d55ec24ff894" />

<img width="1522" height="840" alt="12" src="https://github.com/user-attachments/assets/7134d524-3729-4795-a2f3-24df5874ce4f" />

## 📄 Documentation détaillée

La documentation complète du projet (explications, captures d’écran...)
est disponible sur mon LinkedIn : https://www.linkedin.com/in/abdourahamaneabdelwahab
