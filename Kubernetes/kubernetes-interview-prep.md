# ☸ Kubernetes Interview Preparation Guide

A practical guide for developers and DevOps engineers to ace Kubernetes interviews.

---

# 1️⃣ Basic Questions

**Q: What is Kubernetes?**  
A: Kubernetes (K8s) is a container orchestration platform that automates deployment, scaling, and management of containerized applications.

**Q: Difference between Docker and Kubernetes?**

| Feature           | Docker           | Kubernetes                  |
| ----------------- | ---------------- | --------------------------- |
| Orchestration     | No               | Yes                         |
| Scaling           | Manual           | Automatic                   |
| Deployment        | Single container | Multi-container, multi-node |
| Service Discovery | Limited          | Built-in                    |

**Q: What are Pods?**  
A pod is the smallest deployable unit in Kubernetes, usually containing one or more containers that share networking and storage.

---

# 2️⃣ Core Concepts Questions

**Q: What is a Deployment?**

- Manages ReplicaSets and Pods
- Handles rolling updates & rollbacks

**Q: What is a Service?**  
Exposes Pods internally or externally. Types:

- ClusterIP → internal
- NodePort → external port
- LoadBalancer → cloud load balancer

**Q: What is a ConfigMap?**  
Stores non-sensitive configuration data that Pods can consume.

**Q: What is a Secret?**  
Stores sensitive information (passwords, API keys) safely.

---

# 3️⃣ Intermediate Questions

**Q: What is an Ingress?**  
Manages HTTP/S routing to Services. Acts like a reverse proxy.

**Q: Explain PersistentVolume (PV) and PersistentVolumeClaim (PVC)**

- PV → Storage resource in the cluster
- PVC → Request for storage by a Pod

**Q: What is a Namespace?**  
Logical partition of resources inside a cluster for isolation.

**Q: What is a ReplicaSet?**  
Ensures a specified number of pod replicas are running at any time.

---

# 4️⃣ Advanced Questions

**Q: How do rolling updates work?**  
Kubernetes updates Pods gradually, replacing old Pods with new Pods while ensuring minimal downtime.

**Q: What is a StatefulSet?**  
Used for applications that require stable network identity and persistent storage (databases, queues).

**Q: What is Helm?**  
Kubernetes package manager that simplifies deployment of complex apps.

**Q: What is Horizontal Pod Autoscaler (HPA)?**  
Automatically scales pods based on metrics like CPU or memory usage.

---

# 5️⃣ Troubleshooting & Commands

**Q: How to check pod logs?**

```bash
kubectl logs <pod-name>
```

**Q: How to inspect a pod?**

```bash
kubectl describe pod <pod-name>
```

**Q: How to exec into a container?**

```bash
kubectl exec -it <pod-name> -- bash
```

**Q: How to apply YAML safely?**

```bash
kubectl apply --dry-run=client -f deployment.yaml
```

**Q: How to delete a deployment?**

```bash
kubectl delete deployment <deployment-name>
```

---

# 6️⃣ Scenario-Based Questions

**Scenario 1:** Deploy a Node.js app with a database in Kubernetes

- Answer: Use Deployment for app & database
- Service for database
- ConfigMap/Secret for environment variables
- PersistentVolumeClaim for database storage

**Scenario 2:** Implement zero-downtime updates

- Answer: Rolling updates via Deployment, test with `kubectl rollout status`

**Scenario 3:** Scale app automatically based on traffic

- Answer: Horizontal Pod Autoscaler, metrics API, set min/max replicas

**Scenario 4:** Expose multiple services under one domain

- Answer: Ingress with path-based routing, TLS for HTTPS

---

# 7️⃣ Quick Reference Commands

```bash
kubectl get pods
kubectl get deployments
kubectl get services
kubectl describe pod <pod>
kubectl logs <pod>
kubectl exec -it <pod> -- bash
kubectl apply -f file.yaml
kubectl delete -f file.yaml
kubectl rollout status deployment <name>
```

---

# 🧠 Tips to Crack Interviews

- Understand **architecture**: Control plane vs worker nodes
- Explain **Pod lifecycle**
- Know **YAML structure** for Deployments, Services, ConfigMaps, Secrets
- Demonstrate **hands-on examples**
- Mention **best practices**: namespaces, autoscaling, Ingress, storage
- Always be ready to write **small YAML snippets** on a whiteboard

---

# 📌 Recommended Prep Path

1. Master Pods, Deployments, Services
2. Learn ConfigMaps, Secrets, Volumes
3. Practice rolling updates, HPA
4. Explore Ingress and Helm
5. Try deploying a small full-stack app on Minikube
6. Review common troubleshooting commands
7. Read production deployment strategies

---

# 🚀 Ready for DevOps Interviews

## This guide gives you both theory and practical command knowledge needed for Kubernetes-focused roles.

## 🚀 Quick Navigation

1. [Kubernetes Beginner Roadmap](kubernetes-beginner-roadmap.md) - Step-by-step learning path from zero to production
2. [Kubernetes YAML Cheatsheet](kubernetes-yaml-cheatsheet.md) - Quick reference for writing Kubernetes YAML files
3. [Kubernetes Interview Prep Guide](kubernetes-interview-prep.md) - Common questions, scenarios, and command references for interviews
