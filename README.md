# CI/CD Demo with Jenkins, Docker, and GitHub

This repository is a **practice project** to learn how to set up a Jenkins pipeline that builds and runs a **frontend, backend, and database** using Docker.

## 🚀 Project Structure
ci-cd-demo/
│
├── frontend/ # Simple React placeholder (runs in Node)
│ └── Dockerfile
│
├── backend/ # Simple Express.js API
│ ├── server.js
│ └── Dockerfile
│
├── docker-compose.yml # Orchestrates frontend, backend, and MySQL
├── Jenkinsfile # Jenkins pipeline definition
└── README.md

markdown
Copy code

## 🛠 Technologies Used
- **Jenkins** – CI/CD automation  
- **Docker** – Containerization  
- **Docker Compose** – Multi-container setup  
- **Node.js** – Backend API (Express)  
- **React (placeholder)** – Frontend app  
- **MySQL** – Database  

## ⚡ How It Works
1. Jenkins pulls this repo from GitHub.  
2. Builds Docker images for frontend, backend, and MySQL.  
3. Runs all services using `docker-compose`.  
4. Tests the backend API with `curl`.  
5. Tears down containers after pipeline run.  

## ▶️ Running Locally
```bash
# Build and start services
docker-compose up --build -d

# Stop services
docker-compose down
Backend → http://localhost:3000

Frontend → http://localhost:8080

MySQL → port 3306

📌 Jenkins Pipeline
The Jenkinsfile defines a pipeline with:

Checkout – Clone this repo

Build Images – Build Docker images

Run Containers – Start services

Test Backend – Simple API test

Cleanup – Stop and remove containers

🎯 Goal
This repo is for learning and practicing CI/CD pipelines with Jenkins and Docker on an Ubuntu EC2 instance.
