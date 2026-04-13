# Devops-secure-pipeline
# 🚀 Secure CI/CD Pipeline with Automated Security Gates

## 📌 Project Overview
This project demonstrates how to build a secure CI/CD pipeline using Jenkins, Docker, and security tools like Snyk, Trivy, and Gitleaks.

The pipeline automatically builds, scans, and validates the application before deployment.

---

## 🛠️ Technologies Used
- GitHub (Source Code Management)
- Jenkins (CI/CD Pipeline)
- Docker (Containerization)
- Trivy (Container Security Scan)
- Snyk (Dependency Scanning)
- Gitleaks (Secret Detection)
- AWS EC2 (Hosting)

---

## ⚙️ Prerequisites
Make sure you have:
- AWS EC2 instance (Ubuntu)
- Jenkins installed
- Docker installed
- Git installed
- Node.js & npm installed
- Python3 & pip installed

---

## 📂 Project Structure
. ├── app/ │   └── app.py ├── Dockerfile ├── Jenkinsfile ├── requirements.txt └── README.md

---

## 🔹 Step 1: Setup GitHub Repository

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main

## 🔹 Step 2: Setup Jenkins Job
## 🔹 Step 3: Install Required Tools
Step 3: Install Required Tools
Install Node.js & npm
sudo apt install nodejs npm -y
Install Snyk
npm install -g snyk
snyk auth
Install Trivy
sudo apt install wget apt-transport-https gnupg -y
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo "deb https://aquasecurity.github.io/trivy-repo/deb jammy main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt update
sudo apt install trivy -y
Install Gitleaks
wget https://github.com/gitleaks/gitleaks/releases/latest/download/gitleaks-linux-amd64
chmod +x gitleaks-linux-amd64
sudo mv gitleaks-linux-amd64 /usr/local/bin/gitleaks

## 🔹 Step 4: Build Docker Image
docker build -t myapp .
## 🔹 Step 5: Run security Scans
snyk test --file=requirements.txt
Trivy Scan
trivy image myapp
Secret Scan
gitleaks detect

## 🔹 Step 6: Implement Kill Switch
trivy image --exit-code 1 --severity HIGH,CRITICAL myapp
## 🔹 Step 7: Jenkins Pipeline(Jenkinsfile)
