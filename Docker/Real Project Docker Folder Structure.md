# 🏗 2. Real Project Docker Folder Structure

```
project-root/
│
├── src/
├── public/
├── dist/
│
├── Dockerfile
├── docker-compose.yml
├── nginx.conf
├── .dockerignore
├── .env
├── package.json
└── package-lock.json
```

---

## Example `docker-compose.yml`

```yaml
version: '3.9'

services:
  app:
    build: .
    ports:
      - '8080:80'
    env_file:
      - .env
    restart: unless-stopped
```

---

## 🚀 Quick Navigation

1. [Advanced Docker Production Guide](Advanced%20Docker%20Production%20Guide.md) - In-depth guide for production Docker deployments
2. [Real Project Docker Folder Structure](Real%20Project%20Docker%20Folder%20Structure.md) - Recommended folder organization for Docker projects
3. [Docker + Nginx + Node Production Template](Docker%20+%20Nginx%20+%20Node%20Production%20Template.md) - Complete stack template for Node.js applications
4. [Docker Interview Prep Guide](Docker%20Interview%20Prep%20Guide.md) - Interview preparation material for Docker
