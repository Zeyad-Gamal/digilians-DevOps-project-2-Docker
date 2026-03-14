#  DevOps Dockerized Flask Application

A production-style **DevOps project** that demonstrates how to deploy a scalable Flask application using **Docker, Docker Compose, Nginx, PostgreSQL, and Redis** with **Load Balancing, HTTPS, and Rate Limiting**.

This project simulates a real-world backend infrastructure where multiple Flask instances are deployed behind an Nginx reverse proxy.

---

# 🏗️ Architecture

User Request
↓
Nginx Reverse Proxy (HTTPS + Rate Limiting)
↓
Load Balancer
├── Flask App Instance 1
└── Flask App Instance 2
↓
Redis (Caching)
↓
PostgreSQL (Database)

---

# ✨ Features

* Dockerized microservice architecture
* Nginx Reverse Proxy
* HTTPS with self-signed SSL certificates
* Load Balancing between multiple Flask containers
* PostgreSQL database
* Redis caching layer
* API Rate Limiting
* Static file serving via Nginx
* Production-style Docker setup

---

# 📁 Project Structure

project-root
│
├── Dockerfile
├── docker-compose.yml
├── flask_app.py
├── requirements.txt
├── init.sql
│
├── conf
│   └── nginx.conf
│
├── ssl
│   ├── generate_ssl.sh
│   └── certs
│
└── static
└── style.css

---

# ⚙️ Technologies Used

| Technology     | Purpose                       |
| -------------- | ----------------------------- |
| Docker         | Containerization              |
| Docker Compose | Multi-container orchestration |
| Nginx          | Reverse proxy & load balancer |
| Flask          | Backend API                   |
| PostgreSQL     | Relational database           |
| Redis          | In-memory cache               |
| OpenSSL        | SSL certificate generation    |

---

# 🔧 Prerequisites

Before running the project make sure you have:

* Docker
* Docker Compose
* Git

Check installation:

docker --version
docker compose version

---

# 🚀 Running the Project

## 1️⃣ Clone the repository

git clone <your-repo-url>
cd project-folder

---

## 2️⃣ Generate SSL Certificates

Run the SSL generation script:

chmod +x ssl/generate_ssl.sh
./ssl/generate_ssl.sh

This will generate:

ssl/certs/cert.pem
ssl/certs/key.pem

These certificates are used by **Nginx for HTTPS**.

---

## 3️⃣ Build and start containers

docker compose up --build

Or run in detached mode:

docker compose up -d --build

---

## 4️⃣ Verify running containers

docker ps

You should see containers for:

* nginx
* flask1
* flask2
* postgres
* redis

---

# 🌐 Access the Application

Open your browser:

https://localhost:8081

Since the certificate is **self-signed**, the browser may show a security warning.

---

# 📡 API Testing

Example test using curl:

curl -k https://localhost:8081

The -k flag ignores SSL verification for self-signed certificates.

---

# ⚖️ Load Balancing

Nginx distributes incoming requests between:

flask1
flask2

Using the **least connections algorithm**.

---

# 🛡️ Security Features

### HTTPS Encryption

Traffic is encrypted using SSL certificates.

### Rate Limiting

API requests are limited to prevent abuse.

Example configuration:

limit_req_zone $binary_remote_addr zone=api_limit:10m rate=10r/s;

---

# 🐳 Docker Services

| Service  | Description                       |
| -------- | --------------------------------- |
| nginx    | Reverse proxy and load balancer   |
| flask1   | First Flask application instance  |
| flask2   | Second Flask application instance |
| postgres | PostgreSQL database               |
| redis    | Redis caching service             |

---

# 📦 Static Files

Static files are served directly by **Nginx** for better performance.

Example:

/static/style.css

---

# 🧹 Stopping the Project

Stop containers:

docker compose down

Remove containers and volumes:

docker compose down -v

---

# 💡 DevOps Concepts Demonstrated

This project demonstrates several important DevOps concepts:

* Containerization
* Reverse Proxy
* Load Balancing
* Infrastructure Isolation
* HTTPS Configuration
* Service Orchestration
* Rate Limiting
* Multi-container architecture

---


