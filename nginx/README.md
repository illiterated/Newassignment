📂 nginx/ — Reverse Proxy Setup
This folder contains configuration and setup files for the NGINX reverse proxy used in the Dockerized microservices architecture.

```bash
nginx/
├── nginx.conf      # NGINX configuration for reverse proxy
└── Dockerfile      # Dockerfile to containerize NGINX with custom config
```
What It Does

1. Acts as a reverse proxy to expose both microservices (service1 and service2) through a single public-facing port (8080).
2. Redirects incoming HTTP requests to the appropriate internal services based on URL paths.

📄 nginx.conf Overview

/service1/ routes to your Go microservice (service1) running on port 8001.

/service2/ routes to your Flask+uv microservice (service2) on port 8002.

🐳 Dockerfile (for NGINX container)

  FROM nginx:latest

  COPY nginx.conf /etc/nginx/nginx.conf

This Dockerfile uses the official nginx image and replaces its default configuration with the one in nginx.conf.

How It Integrates
The nginx container is started by docker-compose.yml and depends on service1 and service2.

It makes those services available at:

http://<IP>:8080/service1/hello

http://<IP>:8080/service2/ping

