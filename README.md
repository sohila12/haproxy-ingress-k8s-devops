
# 🚀 HAProxy Ingress Controller on Kubernetes  
**DevOps Project – Production-Ready Deployment (Tested on Kind)**  

![HAProxy](https://img.shields.io/badge/HAProxy-Ingress_Controller-006D8B?style=for-the-badge&logo=haproxy&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.31-326CE5?style=for-the-badge&logo=kubernetes)
![Kind](https://img.shields.io/badge/Tested_with-Kind-00A9E0?style=for-the-badge)

---

## 📌 Project Overview
This project demonstrates a **fully operational deployment** of the **HAProxy Kubernetes Ingress Controller** with complete RBAC, dedicated namespace, secure ServiceAccount, and NodePort exposure using `hostNetwork` mode for full compatibility with **Kind clusters**.

**Deployment Status:** ✅ *Stable & Fully Working*

---

## 🏗️ Architecture Diagram
The following diagram represents the full deployment flow:

![Architecture](diagram.png)

---

## 🧩 Components Deployed

| Component              | Name                                      | Description                                  |
|-----------------------|-------------------------------------------|----------------------------------------------|
| **Namespace**         | `haproxy-controller-devops`               | Isolated environment for all resources       |
| **ServiceAccount**    | `haproxy-service-account-devops`          | Secure identity for the controller           |
| **ClusterRole**       | `haproxy-cluster-role-devops`             | Provides required RBAC permissions           |
| **ClusterRoleBinding**| `haproxy-role-binding-devops`             | Links SA with ClusterRole                    |
| **Default Backend**   | `backend-deployment-devops`               | Uses Google defaultbackend image             |
| **Ingress Controller**| `haproxy-ingress-devops`                  | `haproxytech/kubernetes-ingress:latest`      |
| **NodePort Service**  | `ingress-service-devops`                  | Exposes ports: 32456, 32567, 32678           |

---

## 🌐 Accessing the Services (Kind + hostNetwork)
Get the Kind node IP:

```bash
kubectl get nodes -o wide
Default example: 172.19.0.2

Service	Port	URL	Expected Output
HTTP Traffic	32456	http://172.19.0.2:32456	Default backend (404 page)
HAProxy Stats	32678	http://172.19.0.2:32678	Stats UI (login: admin/admin)

🧾 Proof of Successful Deployment
bash
Copy code
kubectl get all -n haproxy-controller-devops -o wide
Expected:

All Pods Running

Services exposed

Controller logs healthy

🚀 How to Deploy
bash
Copy code
kubectl apply -f manifests/
🧹 Cleanup
bash
Copy code
kubectl delete -f manifests/
👩‍💻 Project Owner
Sohila Hosam – (sohila12)
Environment: Ubuntu 22.04 + Kind + Kubernetes v1.31

✨ Thank you for reviewing my DevOps project!
