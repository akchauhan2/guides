# 🐳 3. Docker + Nginx + Node Production Template

## Dockerfile

```dockerfile
# ---------- Build ----------
FROM node:22-alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# ---------- Production ----------
FROM nginx:alpine

RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

---

## nginx.conf (SPA Safe)

```nginx
server {
    listen 80;

    location / {
        root /usr/share/nginx/html;
        index index.html;
        try_files $uri $uri/ /index.html;
    }
}
```

---

## Run

```bash
docker build -t my-app .
docker run -d -p 8080:80 --name my-app my-app
```

---

## 🚀 Quick Navigation

1. [Advanced Docker Production Guide](Advanced%20Docker%20Production%20Guide.md) - In-depth guide for production Docker deployments
2. [Real Project Docker Folder Structure](Real%20Project%20Docker%20Folder%20Structure.md) - Recommended folder organization for Docker projects
3. [Docker + Nginx + Node Production Template](Docker%20+%20Nginx%20+%20Node%20Production%20Template.md) - Complete stack template for Node.js applications
4. [Docker Interview Prep Guide](Docker%20Interview%20Prep%20Guide.md) - Interview preparation material for Docker
