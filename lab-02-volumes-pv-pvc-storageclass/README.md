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
