# HAProxy Ingress Controller - DevOps Project

## Project Status: ✅ Fully Working on Kind

### Components Created
- Namespace: haproxy-controller-devops
- RBAC (ServiceAccount + ClusterRole + ClusterRoleBinding)
- Default Backend Deployment + Service
- HAProxy Ingress Controller Deployment (with hostNetwork & privileged)
- NodePort Service (32456, 32567, 32678)

### Proof of Working
- Both pods are 1/1 Running
- Tested successfully on Kind cluster

### Access (hostNetwork mode)
Use node IP: 172.19.0.2
- HTTP → 32456 (default backend 404)
- Stats → 32678 (admin/admin)

### Cleanup
```bash
kubectl delete -f manifests/
Done by Sohila Hosam (sohila12) ❤️
