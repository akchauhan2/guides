# ☸ Kubernetes YAML Cheatsheet

A quick reference for writing Kubernetes YAML files for common objects.

---

# 1️⃣ Pods

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: my-app
spec:
  containers:
    - name: my-container
      image: nginx:latest
      ports:
        - containerPort: 80
```

---

# 2️⃣ Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: my-app:latest
          ports:
            - containerPort: 80
```

**Key points:**

- `replicas` → number of pods
- `selector` → matches pod labels
- `template` → pod specification

---

# 3️⃣ Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP # Options: ClusterIP, NodePort, LoadBalancer
```

---

# 4️⃣ ConfigMap

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config
data:
  APP_MODE: production
  API_URL: https://api.example.com
```

---

# 5️⃣ Secret

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
stringData:
  DB_PASSWORD: supersecret
```

---

# 6️⃣ PersistentVolume (PV)

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /mnt/data
```

---

# 7️⃣ PersistentVolumeClaim (PVC)

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

---

# 8️⃣ Ingress

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
    - host: my-app.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: my-service
                port:
                  number: 80
```

---

# 9️⃣ Horizontal Pod Autoscaler (HPA)

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: my-app-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: my-deployment
  minReplicas: 2
  maxReplicas: 5
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 50
```

---

# 10️⃣ Common Commands

```bash
kubectl apply -f file.yaml      # Apply changes
kubectl delete -f file.yaml     # Delete resource
kubectl get pods                # List pods
kubectl get deployments         # List deployments
kubectl get services            # List services
kubectl describe pod my-pod     # Inspect pod
kubectl logs my-pod             # View logs
```

---

# 🧠 Tips

- Always use `apiVersion` compatible with your K8s version
- Labels and selectors must match
- Use `namespace` to isolate environments
- Keep secrets out of YAML when possible (use GitHub Secrets or Vault)
- Validate YAML with `kubectl apply --dry-run=client -f file.yaml`

---

## 🚀 Quick Navigation

1. [Kubernetes Beginner Roadmap](kubernetes-beginner-roadmap.md) - Step-by-step learning path from zero to production
2. [Kubernetes YAML Cheatsheet](kubernetes-yaml-cheatsheet.md) - Quick reference for writing Kubernetes YAML files
3. [Kubernetes Interview Prep Guide](kubernetes-interview-prep.md) - Common questions, scenarios, and command references for interviews
