#  Dockerized Microservices Project with NGINX Reverse Proxy

This project demonstrates how to containerize two microservices (Go & Python) using Docker, manage them with Docker Compose, and expose them via NGINX as a reverse proxy.

---

## 📂 Project Structure

```bash
Newassignment/
├── service_1/        # Go-based microservice
│   ├── main.go
│   └── Dockerfile
├── service_2/        # Python Flask microservice using UV
│   ├── app.py
│   └── Dockerfile
├── nginx/            # NGINX reverse proxy configuration
│   ├── nginx.conf
│   └── Dockerfile
├── docker-compose.yml  # Manages all 3 containers
└── README.md           # Project guide
```

## ⚙️ How It Works

### 🔧 Microservices
- **service_1**: Written in Go (exposed on port `8001`)
- **service_2**: Python app using Flask + [uv](https://astral.sh/blog/introducing-uv/) for faster script management (exposed on port `8002`)

### 🌐 NGINX Reverse Proxy
- Acts as a front-facing server exposed on **port 8080**
- Routes incoming traffic to:
  - `/service1/` → Go app (`http://service1:8001/`)
  - `/service2/` → Python app (`http://service2:8002/`)

### 🐳 Docker Compose
- Brings up all services with **one command**
- Manages networking so containers can talk to each other by name (like `service1`, `service2`)

---

## 🚀 How to Run the Project

### Step-by-step

1. **Clone the repository**
   ```bash
   git clone https://github.com/illiterated/Newassignment.git
   cd Newassignment

   docker-compose up -d

2. **Start the entire system**
   docker-compose up -d

3. **Access Service via Browser**
   http://localhost:8080/service1/hello
   http://localhost:8080/service2/ping

   





