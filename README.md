🚀 End-to-End CI/CD Deployment of Containerized MEAN Stack Application

This project demonstrates a production-grade DevOps implementation of a full-stack MEAN (MongoDB, Express, Angular, Node.js) application using Docker, Docker Compose, Nginx, AWS EC2, GitHub Actions CI/CD, and Docker Hub.

The entire application is fully containerized and deployed with zero manual intervention using CI/CD.

🏗️ Architecture Overview

Browser (Port 80)
→ Nginx (Reverse Proxy)
→ Frontend (Angular)
→ Backend (Node.js / Express)
→ MongoDB

🧰 Tech Stack

Frontend: Angular
Backend: Node.js + Express
Database: MongoDB
Reverse Proxy: Nginx
Containerization: Docker, Docker Compose
CI/CD: GitHub Actions
Cloud: AWS EC2
Registry: Docker Hub
OS: Linux (Ubuntu)

📂 Project Structure

Devops-project-1/
├── backend/
│ ├── Dockerfile
│ └── ...
├── frontend/
│ ├── Dockerfile
│ └── ...
├── nginx/
│ └── default.conf
├── docker-compose.yml
└── .github/
└── workflows/
└── ci-cd.yml

🐳 Docker Images

Images are built and pushed to Docker Hub automatically via CI/CD:

huzaifa8901/frontend:latest
huzaifa8901/backend:latest

⚙️ Local Development Setup

Step 1: Clone Repository

git clone https://github.com/huzaiifa-1/Devops-project-1.git

cd Devops-project-1

Step 2: Install Docker & Docker Compose

sudo apt update
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker $USER
newgrp docker

Step 3: Run Application

docker-compose up -d

Step 4: Verify

docker ps

Open in browser:

http://localhost

☁️ AWS EC2 Deployment

Step 1: Create EC2 Instance

OS: Ubuntu 20.04 or later

Open inbound ports in Security Group:

22 (SSH)

80 (HTTP)

Step 2: Install Docker on EC2

sudo apt update
sudo apt install docker.io docker-compose -y
sudo systemctl start docker
sudo usermod -aG docker $USER
newgrp docker

Step 3: Login to Docker Hub

docker login

Step 4: Clone Repo on EC2

git clone https://github.com/huzaiifa-1/Devops-project-1.git

cd Devops-project-1

Step 5: Start Application

docker-compose pull
docker-compose up -d

Step 6: Access Application

http://<EC2_PUBLIC_IP>

🔁 CI/CD Pipeline (GitHub Actions)

The CI/CD pipeline is defined in:

.github/workflows/ci-cd.yml

On every push to the main branch:

Builds Docker images for frontend and backend

Pushes images to Docker Hub

SSH into EC2 instance

Runs:
docker-compose pull
docker-compose up -d

🔐 GitHub Secrets Used

DOCKERHUB_USERNAME → Docker Hub username
DOCKERHUB_TOKEN → Docker Hub access token
EC2_HOST → EC2 public IP
EC2_SSH_KEY → EC2 private SSH key

🔄 Deployment Flow

Git Push
→ GitHub Actions
→ Build Images
→ Push to Docker Hub
→ SSH into EC2
→ docker-compose pull
→ docker-compose up -d
→ New Version Live

🛡️ Key DevOps Concepts Demonstrated

Full containerization
Multi-stage Docker builds
Nginx reverse proxy
Infrastructure as Code
Immutable deployments
Automated CI/CD
Cloud deployment on AWS EC2
Zero manual deployment steps

🧪 Useful Commands

Stop everything:
docker-compose down

Restart stack:
docker-compose restart

View logs:
docker logs nginx
docker logs backend

Check running containers:
docker ps
