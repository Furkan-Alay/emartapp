# 📦 EMart Microservices Application

Welcome to the **EMart Microservices Project** — a containerized e-commerce application built with a microservices architecture using **Docker** and **Docker Compose**.

---

## 📌 Project Overview

This project containerizes a microservices-based e-commerce site. You can easily deploy and run your own system by making necessary adjustments in the source code.

---

## 📥 Requirements

- **Git Bash** terminal (for Windows)
- **Visual Studio Code**
- **Docker Engine** & **Docker Compose**
- An **AWS Account** (optional if deploying locally)

---

## 📦 Project Structure

- **client/** — Frontend application
- **javaapi/** — Java-based backend API service
- **nodeapi/** — Node.js-based backend API service
- **kkartchart/** — Additional microservice
- **nginx/** — Reverse proxy configuration
- **docker-compose.yaml** — Docker Compose configuration file
- **Dockerfile** — Custom container image builds
- **Jenkinsfile** — CI/CD pipeline configuration (optional)

---

## 🚀 How to Deploy on AWS EC2

1. Create an AWS EC2 instance  
   - Choose **Ubuntu AMI**
   - Instance Type: `t3.medium`
   - Key Pair: Generate a new **.pem** key file
   - Network Settings:  
     - Enable **My IP** access  
     - Allow **HTTP traffic from the internet**
   - Set **Root Volume** to **20GB**
   - Add the following **User Data** script during instance setup:

```bash
#!/bin/bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo usermod -a -G docker ubuntu
```
