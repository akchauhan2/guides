# 📦 4. Docker Interview Prep Guide

## 🔥 Basic Questions

**Q: What is Docker?**
A containerization platform to package applications with dependencies.

**Q: Difference between Image and Container?**

- Image = blueprint
- Container = running instance

**Q: What is Dockerfile?**
A script to build Docker images.

---

## ⚙ Intermediate Questions

**Q: What is multi-stage build?**
A way to reduce final image size by separating build and runtime.

**Q: Difference between CMD and ENTRYPOINT?**

- `CMD` → default command
- `ENTRYPOINT` → fixed command

---

## 🧠 Advanced Questions

**Q: How to reduce Docker image size?**

- Multi-stage builds
- Alpine images
- Remove cache
- `.dockerignore`

**Q: How does Docker networking work?**

- Bridge (default)
- Host
- Overlay (Swarm/K8s)

**Q: What is Docker volume vs bind mount?**

- Volume → Managed by Docker
- Bind mount → Direct local path

---

## 🚀 Real-World Scenario Question

**Q: How would you deploy a Node app in production?**

Answer:

1. Multi-stage build
2. Use `npm ci`
3. Serve static via Nginx
4. Use environment variables
5. Add health checks
6. Use docker-compose
7. Enable restart policy

---

# 🧠 If You're a Working Developer

Your production stack usually looks like:

- App (Node)
- Reverse proxy (Nginx)
- Database (Postgres / Mongo)
- Redis
- Docker Compose
- CI/CD pipeline
-

---

## 🚀 Quick Navigation

1. [Advanced Docker Production Guide](Advanced%20Docker%20Production%20Guide.md) - In-depth guide for production Docker deployments
2. [Real Project Docker Folder Structure](Real%20Project%20Docker%20Folder%20Structure.md) - Recommended folder organization for Docker projects
3. [Docker + Nginx + Node Production Template](Docker%20+%20Nginx%20+%20Node%20Production%20Template.md) - Complete stack template for Node.js applications
4. [Docker Interview Prep Guide](Docker%20Interview%20Prep%20Guide.md) - Interview preparation material for Docker
