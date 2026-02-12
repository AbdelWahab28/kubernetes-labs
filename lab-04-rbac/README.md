# Lab 04 – Kubernetes RBAC (Role-Based Access Control)

## 🧠 Objectif
Ce projet a pour objectif de comprendre la gestion des permissions dans Kubernetes à travers le mécanisme RBAC (Role-Based Access Control).

Il démontre comment :

- Créer un ServiceAccount
- Définir un Role avec des permissions spécifiques
- Associer un Role à un utilisateur ou ServiceAccount via un RoleBinding
- Restreindre l’accès aux ressources dans un namespace
---

## 🛠️ Technologies utilisées
- Kubernetes (Minikube)
- RBAC
- ServiceAccount
- Role
- RoleBinding
- kubectl

---

## 📁 Structure du lab
```bash
lab-04-rbac/
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
│  ├─rbac/
│     ├─roles.yaml            # Role pour laravel et mysql
│     ├─rolebindings.yaml     # 
└─ README.md
```
## Déploiement et exécution

1️⃣ Démarrage du cluster Minikube
```bash
minikube start
kubectl get nodes
```
2️⃣ Creation namespaces
```bash
kubectl create namespace dev
kubectl create namespace prod
kubectl get namespaces
```
3️⃣ creation serviceAccount
```bash
kubectl create serviceacount laravel-sa -n dev
kubectl create serviceaccount mysql-sa -n dev
kubectl get serviceaccount -n dev
```
4️⃣ Creation des roles
```bash
nano roles.yaml
nano rolebindings.yaml
kubectl apply -f rbac/roles.yaml
kubectl apply -f rbac/rolebindings.yaml
```
5️⃣ Deploiment
```bash
kubectl apply -f configmap.yaml -n dev
kubectl apply -f secret.yaml -n dev
kubectl apply -f mysql-pvc.yaml -n dev
kubectl apply -f mysql-deployment.yaml -n dev
kubectl apply -f manifestk8s/laravel-deployment.yaml -n dev
kubectl auth can-i get pods --as=system:serviceaccount:dev:laravel-sa -n dev
kubectl auth can-i delete pods --as=system:serviceaccount:dev:laravel-sa -n dev
kubectl auth can-i delete pods --as=system:serviceaccount:dev:mysql-sa -n dev
```

## 🧹 Nettoyage du lab
```bash
kubectl delete -f pod.yaml
kubectl delete -f rolebinding.yaml
kubectl delete -f role.yaml
kubectl delete -f serviceaccount.yaml
kubectl delete -f namespace.yaml
minikube stop
```

<img width="683" height="431" alt="11" src="https://github.com/user-attachments/assets/5abf0978-3270-46a4-b450-1a89b2e09688" />

<img width="500" height="392" alt="12" src="https://github.com/user-attachments/assets/6ebce3c3-dd95-4348-8c33-6e9f8815a85c" />

<img width="1541" height="257" alt="9" src="https://github.com/user-attachments/assets/3ea7ab2c-2ffa-4b8d-8e4f-2d7887a9a8b2" />

<img width="1537" height="193" alt="10" src="https://github.com/user-attachments/assets/dbca5d16-121b-4f87-84d2-a0b751ae7590" />

## 📄 Documentation détaillée

La documentation complète du projet (explications, captures d’écran...)
est disponible sur mon LinkedIn : https://linkedin.com/in/abdelwahab28

