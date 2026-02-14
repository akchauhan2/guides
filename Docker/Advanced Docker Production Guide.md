# 📘 1. Advanced Docker Production Guide (Best Practices)

## 🧱 1. Use Multi-Stage Builds

Reduces image size drastically.

```dockerfile
# Build stage
FROM node:22-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Production stage
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]
```

---

## 📦 2. Use `npm ci` Instead of `npm install`

- Faster
- Deterministic builds
- Uses `package-lock.json`

---

## 🧹 3. Use `.dockerignore`

```dockerignore
node_modules
.git
.env
dist
Dockerfile
docker-compose.yml
```

Prevents large context upload.

---

## 🔒 4. Don’t Run as Root

```dockerfile
RUN addgroup -S app && adduser -S app -G app
USER app
```

Security best practice.

---

## 🏷 5. Use Specific Image Tags

❌ Bad:

```dockerfile
FROM node:latest
```

✅ Good:

```dockerfile
FROM node:22.3-alpine
```

---

## 📉 6. Keep Image Small

- Use `alpine`
- Remove cache
- Multi-stage builds
- Avoid unnecessary tools

---

## 🔄 7. Use Health Checks

```dockerfile
HEALTHCHECK CMD curl --fail http://localhost:80 || exit 1
```

---

## 🌍 8. Use Environment Variables

Never hardcode secrets.

```bash
docker run -e NODE_ENV=production my-app
```

---

## 🚀 Quick Navigation

1. [Advanced Docker Production Guide](Advanced%20Docker%20Production%20Guide.md) - In-depth guide for production Docker deployments
2. [Real Project Docker Folder Structure](Real%20Project%20Docker%20Folder%20Structure.md) - Recommended folder organization for Docker projects
3. [Docker + Nginx + Node Production Template](Docker%20+%20Nginx%20+%20Node%20Production%20Template.md) - Complete stack template for Node.js applications
4. [Docker Interview Prep Guide](Docker%20Interview%20Prep%20Guide.md) - Interview preparation material for Docker
