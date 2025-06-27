This project demonstrates how to containerize two microservices (Go & Python) using Docker, manage them with Docker Compose, and expose them via NGINX as a reverse proxy.

# 🧰 Prerequisites
Before running this project, ensure you have the following installed on your system:

✅ Git – for cloning the repository
#  Dockerized Microservices Project with NGINX Reverse Proxy
```bash
sudo apt update && sudo apt install git -y
```
✅ Docker – to build and run containers
Install Docker using the official script:
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```
✅ Docker Compose – to orchestrate multi-container apps
Install Docker Compose:
```bash
sudo apt install docker-compose -y
```
✅ Expose port 8080 in AWS EC2 – Make sure your EC2 Security Group allows inbound traffic on port 8080.

✅ (Optional) Public IP or Domain – If hosting on a cloud VM, know your instance's public IP.

bash
Copy code


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

   





