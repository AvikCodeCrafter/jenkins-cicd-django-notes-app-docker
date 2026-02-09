# 🚀 Django CI/CD Pipeline using Jenkins, Docker & AWS EC2

An end-to-end **CI/CD pipeline** for a Django application using **Jenkins**, **Docker**, and **AWS EC2**, demonstrating real-world DevOps practices including automated builds, containerization, image publishing, and cloud deployment.

---

## 🧩 Architecture Overview

![CI/CD Architecture](jenkins_docker_ec2_cicd.png)

---

## 🛠 Tech Stack

- **Source Control:** GitHub (HTTPS, public repository)
- **CI/CD Tool:** Jenkins (Declarative Pipeline)
- **Containerization:** Docker
- **Image Registry:** Docker Hub
- **Cloud Platform:** AWS EC2 (Amazon Linux 2023)
- **Application Framework:** Django
- **Database:** MySQL (Docker-based for testing)

---

## 🔁 High-Level CI/CD Workflow (End-to-End)

This project implements a complete **CI/CD pipeline** for a Django application, from code commit to live deployment on AWS EC2.

### 🔹 What actually happens

1. Developer pushes code to **GitHub** (public repository)
2. **Jenkins pipeline** is triggered (manual trigger or SCM polling)
3. Jenkins **clones source code over HTTPS**
4. Jenkins **builds a Docker image** using the application `Dockerfile`
5. Docker image is **tagged and pushed to Docker Hub**
6. Jenkins **deploys the Docker container on AWS EC2**
7. Django application **runs inside a Docker container**
8. Application port **8000** is exposed
9. Application becomes accessible via:

```
http://<EC2_PUBLIC_IP>:8000
```

---

## 🧠 What this pipeline demonstrates

### ✅ Continuous Integration (CI)
- Automated source code checkout
- Docker image build on every pipeline run
- Consistent and repeatable builds

### ✅ Continuous Deployment (CD)
- Automated Docker image publishing
- Automated container deployment on EC2
- Zero manual intervention after pipeline trigger

### ✅ Real Cloud Runtime
- Application runs on **real AWS EC2 infrastructure**
- Amazon Linux 2023 as the host OS
- Production-like Docker deployment model

---

## 🧪 Jenkins Pipeline Stages

- **Code Clone**
  - Pulls latest source code from GitHub over HTTPS

- **Build Image**
  - Builds Docker image for the Django application

- **Push to Docker Hub**
  - Authenticates using Jenkins credentials
  - Tags and pushes image to Docker Hub

- **Deploy**
  - Runs the Docker container on AWS EC2
  - Maps container port `8000` to host port `8000`

---

## 📦 Docker Image

```
thatgeekcontainer/django-notes-app:latest
```

---

## ▶️ Run Application Locally (Optional)

```bash
docker build -t django-notes-app .
docker run -d -p 8000:8000 django-notes-app
```

---

## 🧠 Key Learnings & Troubleshooting Experience

- Designed a full CI/CD pipeline using **Jenkins Declarative Pipeline**
- Built and deployed Dockerized Django applications
- Debugged real-world issues including:
  - GitHub HTTPS outages (HTTP 500 errors)
  - Jenkins SCM checkout failures
  - Docker container exiting due to missing CMD
  - Django runtime failures caused by database misconfiguration
- Understood Docker container lifecycle and process management
- Gained hands-on experience deploying applications on **AWS EC2**

---

## 🚀 Future Enhancements

- Replace Docker Hub with **AWS ECR**
- Deploy using **ECS or EKS**
- Use **Gunicorn + Nginx** for production workloads
- Add **GitHub Webhooks** for automatic triggers
- Introduce **Docker Compose** for multi-container setup
- Implement image versioning and rollback strategy
- Add monitoring and logging

---

## 👨‍💻 Author

**Avik Banerjee**  
Cloud / DevOps Engineer  
AWS Certified | Jenkins | Docker | CI/CD

---

## ⭐ Resume Highlight

> Built and deployed an end-to-end CI/CD pipeline using Jenkins, Docker, and AWS EC2 for a Django application, enabling automated image builds, registry publishing, and cloud-based container deployment.
