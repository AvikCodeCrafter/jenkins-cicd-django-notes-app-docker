# 🚀 Django CI/CD Pipeline using Jenkins, Docker & AWS EC2

An end-to-end **CI/CD pipeline** for a Django application using **Jenkins**, **Docker**, and **AWS EC2**, demonstrating real-world DevOps practices including containerization, automated builds, image publishing, and cloud deployment.

---

## 🧩 Architecture Overview

![CI/CD Architecture](jenkins_docker_ec2_cicd.png)

---

## 🛠 Tech Stack

- **Source Control:** GitHub (HTTPS)
- **CI/CD:** Jenkins (Declarative Pipeline)
- **Containerization:** Docker
- **Image Registry:** Docker Hub
- **Cloud Platform:** AWS EC2 (Amazon Linux 2023)
- **Application:** Django
- **Database:** MySQL (Docker-based for testing)

---

## 🔄 CI/CD Workflow

1. Developer pushes code to **GitHub**
2. **Jenkins Pipeline** is triggered
3. Jenkins:
   - Clones the repository
   - Builds Docker image using `Dockerfile`
   - Tags and pushes image to **Docker Hub**
4. Jenkins deploys the image on **AWS EC2**
5. Django application runs as a Docker container
6. Application is accessible via:

```
http://<EC2_PUBLIC_IP>:8000
```

---

## 🧪 Pipeline Stages

- **Code Clone** – Pulls source code from GitHub
- **Build Image** – Builds Docker image for Django app
- **Push to Docker Hub** – Pushes image securely using Jenkins credentials
- **Deploy** – Runs the container on AWS EC2

---

## 📦 Docker Image

```
thatgeekcontainer/django-notes-app:latest
```

---

## ▶️ Run Locally (Optional)

```bash
docker build -t django-notes-app .
docker run -d -p 8000:8000 django-notes-app
```

---

## 🧠 Key Learnings

- Implemented a real-world **CI/CD pipeline** using Jenkins
- Built and deployed Dockerized Django applications
- Debugged GitHub HTTPS outages and Docker runtime issues
- Understood Docker container lifecycle and deployment behavior
- Gained hands-on experience with AWS EC2 production deployment

---

## 🚀 Future Enhancements

- Migrate Docker Hub to **AWS ECR**
- Deploy containers using **ECS / EKS**
- Use **Gunicorn + Nginx** for production
- Implement **GitHub Webhooks**
- Add **Docker Compose / Kubernetes**
- Add image versioning and rollback strategies

---

## 👨‍💻 Author

**Avik Banerjee**  
Cloud / DevOps Engineer  
AWS Certified | Jenkins | Docker | CI/CD

---

## ⭐ Resume Highlight

> Built and deployed an end-to-end CI/CD pipeline using Jenkins, Docker, and AWS EC2 for a Django application, enabling automated builds, image publishing, and cloud deployment.
