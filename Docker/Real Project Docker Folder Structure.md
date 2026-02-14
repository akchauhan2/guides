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
