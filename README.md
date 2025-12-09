# 🚀 HAProxy Ingress Controller on Kubernetes  
**DevOps Project – Production-Ready Deployment (Tested on Kind)**

## 📌 Project Overview
This project demonstrates a fully operational deployment of the **HAProxy Kubernetes Ingress Controller** with full RBAC, a dedicated namespace, a secure ServiceAccount, and NodePort access via `hostNetwork` mode for seamless operation on Kind clusters.

**Deployment Status: ✅ Stable & Fully Working**

## 🏗️ Architecture Diagram
![Architecture Diagram](diagram.png)

## 🧩 Components Deployed

| Component                | Name                                      | Description                                      |
|--------------------------|-------------------------------------------|--------------------------------------------------|
| Namespace                | `haproxy-controller-devops`               | Isolated environment for all resources           |
| ServiceAccount           | `haproxy-service-account-devops`          | Controller identity & access permissions        |
| ClusterRole              | `haproxy-cluster-role-devops`             | Required RBAC permissions                        |
| ClusterRoleBinding       | `haproxy-cluster-role-binding-devops`     | Binds ServiceAccount with ClusterRole            |
| Default Backend          | `backend-deployment-devops`               | Uses Google defaultbackend image                 |
| Ingress Controller       | `haproxy-ingress-devops`                  | Runs `haproxytech/kubernetes-ingress:latest`     |
| NodePort Service         | `ingress-service-devops`                  | Exposes ports 32456, 32567, 32678                 |

## 🌐 Accessing the Services (Kind + hostNetwork)

Get the Kind node IP:
```bash
kubectl get nodes -o wide
Service,Port,URL,Expected Output
HTTP Traffic,32456,http://<NODE-IP>:32456,Default backend (404 page)
HAProxy Stats,32678,http://<NODE-IP>:32678,Stats UI (admin/admin)
🧾 Proof of Successful Deployment
Bashkubectl get all -n haproxy-controller-devops -o wide
Expected:

✔️ All pods running (1/1)
✔️ Services exposed correctly
✔️ Controller logs healthy

Proof
🚀 How to Deploy
Bashkubectl apply -f manifests/
🧹 Cleanup
Bashkubectl delete -f manifests/
👩‍💻 Project Owner
Sohila Hosam – @sohila12
Environment: Ubuntu 22.04 • Kind • Kubernetes v1.31
✨ Thank you for reviewing my DevOps project!
