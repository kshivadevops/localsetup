# 🚀 DevSecOps Environment Setup on Ubuntu (WSL)

![Ubuntu](https://img.shields.io/badge/Ubuntu-20.04%2B-blue?logo=ubuntu) ![Docker](https://img.shields.io/badge/Docker-Installed-blue?logo=docker) ![Kubernetes](https://img.shields.io/badge/Kubernetes-Minikube-blue?logo=kubernetes) ![Jenkins](https://img.shields.io/badge/Jenkins-Running%20on%20Docker-orange?logo=jenkins) ![SonarQube](https://img.shields.io/badge/SonarQube-Static%20Code%20Analysis-yellow?logo=sonarqube)

> Complete guide to setting up a modern DevSecOps lab on Ubuntu (via WSL2), including Docker, Kubernetes, Jenkins, SonarQube, Git, Maven, Trivy, Ansible, Terraform, and AWS CLI.
---

## 🔧 1. Ubuntu on WSL Setup

```bash
wsl --install -d Ubuntu-24.04
```

```bash
sudo apt update && sudo apt upgrade -y
```

## 🔧 2. Install Docker

```bash
sudo apt install -y ca-certificates curl gnupg
```

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```bash
echo "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
sudo apt update
```

```bash
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```bash
sudo usermod -aG docker $USER && newgrp docker
```

## 🔧 3. Install Minikube & kubectl

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

```bash
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

```bash
chmod +x kubectl && sudo mv kubectl /usr/local/bin/
```

## 🔧 4. Run Jenkins on Docker

```bash
docker run -d --name jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
```

## 🔧 5. Run SonarQube on Docker

```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube
```

## 🔧 6. Install Git and Maven

```bash
sudo apt install -y git maven
```

## 🔧 7. Install Trivy

```bash
sudo apt install -y wget
```

```bash
wget https://github.com/aquasecurity/trivy/releases/download/v0.44.0/trivy_0.44.0_Linux-64bit.deb
```

```bash
sudo dpkg -i trivy_0.44.0_Linux-64bit.deb
```

## 🔧 8. Install Ansible

```bash
sudo apt update
```

```bash
sudo apt install -y ansible
```

## 🔧 9. Install Terraform

```bash
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl
```

```bash
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```

```bash
sudo apt update && sudo apt install -y terraform
```

## 🔧 10. Install AWS CLI

```bash
sudo apt install -y unzip curl
```

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

```bash
unzip awscliv2.zip
```

```bash
sudo ./aws/install
```

---
**Author:** Shiva | DevSecOps Engineer | [LinkedIn](https://www.linkedin.com/)