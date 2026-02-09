# Lab 02 – Kubernetes Volumes : PV, PVC & StorageClass

## 🧠 Objectif
Ce projet a pour but de comprendre la **gestion du stockage persistant** dans Kubernetes
à travers les **PersistentVolumes (PV)**, **PersistentVolumeClaims (PVC)** et les **StorageClass**.

Il démontre comment un pod peut utiliser un volume persistant,
même après un redémarrage.

---

## 🛠️ Technologies utilisées
- Kubernetes (Minikube)
- Volumes persistants
- PV / PVC
- StorageClass
- Nginx (pod de test)

---

## 📁 Structure du lab
```bash
lab-02-volumes-pv-pvc-storageclass/
├── pv.yaml
├── pvc.yaml
├── pod.yaml
├── storageclass.yaml
└── README.md
```
## Déploiement et exécution

1️⃣ Démarrage du cluster Minikube
```bash
minikube start
kubectl get nodes
```
2️⃣ Créer le PersistentVolume
```bash
kubectl create -f pv.yaml
kubectl get pv
```
3️⃣ Créer le PersistentVolumeClaim
```bash
kubectl create -f pvc.yaml
kubectl get pvc
```
4️⃣ Créer le StorageClass
```bash
kubectl create -f storageclass.yaml
kubectl get sc
```
5️⃣ Déploiement d’un Pod utilisant le PV
```bash
kubectl apply -f pod-pvc.yaml
kubectl get pods
```

## 🧹 Nettoyage du lab
```bash
kubectl delete -f pv.yaml
kubectl delete -f pvc.yaml
kubectl delete -f storageclass.yaml
kubectl delete -f pod-pvc.yaml
minikube stop
```
