# CloudNexus: End-to-End DevOps Pipeline Implementation

![License](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)

**Complete implementation of a DevOps pipeline for a web application using modern practices: CI/CD, Infrastructure as Code, Kubernetes, and GitOps.**

## 📖 Project overview

This project demonstrates the full deployment cycle of a cloud-native application (Todo App) using a modern DevOps stack. The goal is to create a reliable, automated, and secure pipeline from code to production.

**👨‍💻 Author:** Pavlo \
**📧 Контакт:** [paul.antonenko.w@gmail.com](paul.antonenko.w@gmail.com) | [LinkedIn](https://www.linkedin.com/in/pavlo-antonenko/) \
**🚀 Live Demo:** _Add link after deployment_

---

## 🏗 System architecture

_At this stage the architecture is in the planning stage. I will update this section once the next stages are completed.._

### Planned components:
1. **Source code:** GitHub repository with branching using the GitFlow strategy
2. **CI/CD:** GitHub Actions for building, testing, and scanning images
3. **Insult register:** DockerHub
4. **Infrastructure (IaC):** AWS (EC2, VPC, S3), deployed using Terraform
5. **Containerization:** Docker
6. **Orchestration:** Kubernetes (k3s or Minikube for local testing)
7. **Monitoring:** Prometheus/Grafana for metrics collection and visualization

---

## ⚙️ Technology stack

| Category | Technologies |
|-----------|------------|
| **Cloud** | AWS (EC2, VPC, IAM, S3) |
| **Infrastructure as Code** | Terraform |
| **CI/CD** | GitHub Actions |
| **Containers** | Docker |
| **Orchestration** | Kubernetes |
| **Web Servers** | Nginx |
| **Programming** | Node.js, React |
| **Version Control** | Git, GitHub |

---

## 📂 Repository structure (current state)

devops-portfolio-project/
├── app/
│   ├── backend/
│   └── frontend/
├── infrastructure/
│   └── terraform/
├── kubernetes/
│   └── base/
├── .github/workflows/
└── README.md

---

## 🚀 Current status

### ✅ Stage 0: Preparation (Completed)
- [x] A public GitHub repository has been created
- [x] Folder structure initialized
- [x] Added the base code of the application (backend on Node.js and frontend on React)
- [x] `master` branch configured

### 🔄 Next steps:
- [ ] Stage 1: Set up CI/CD with GitHub Actions
- [ ] Stage 2: Infrastructure as Code (IaC) with Terraform
- [ ] Stage 3: Containerization with Docker
- [ ] Stage 4: Deploy to Kubernetes
- [ ] Stage 5: Monitoring and logging

---

## 🚀 How to run a project locally

The instructions below will allow you to run a copy of the project on your local computer for development and testing.

### Prerequisites:

Before you start, make sure that your computer has:
*   **Node.js** (version 16 or higher) - runtime environment for JavaScript.
*   **npm** - package manager, installed with Node.js.
*   **Git** - to clone the repository.

**How to check?** Run in terminal:
```bash
   node --version
   npm --version
   git --version
```
### Steps to start:
<details>
<summary>Clone the repository:</summary>
  
```bash
   git clone https://github.com/cicero-w/devops-portfolio-project.git
   cd your-repository
```
</details>
<details>
<summary>Start the backend (API server)</summary>
+ Open a terminal and go to the backend folder:

```bash
   cd app/backend
```
+ Install dependencies:

```bash
  npm install
```
+ Start the server:

```bash
  npm run dev
```
+ The server will start on port `3000`: `http://localhost:3000`
</details>
<details>
<summary>Launch the frontend (client side):</summary>
+ Open a new terminal (so as not to stop the backend) and go to the frontend folder:

```bash
  cd app/frontend
```
+ Install dependencies:

```bash
  npm install
```
+ Launch the client:

```bash
  npm run dev
```
+ The application will automatically open in the browser on the port `5173`: `http://localhost:5173`
</details>

---

## 📊 System operation screenshots

<details>
<summary>Project structure in IDE</summary>
![Project Structure in IDE](docs/images/stage-0-ide-structure.png)
*Створена структура папок відповідає плану. Видно папки `app/backend`, `app/frontend`, `infrastructure/` та інші.*
</details>

<details>
<summary>Command line with structure</summary>
![Terminal Tree Command](docs/images/stage-0-terminal-tree.png)
*Вивід команди `tree`, що підтверджує логічну організацію файлів проекту.*
</details>

<details>
<summary>A working application in the browser</summary>
![Local Application Running](docs/images/stage-0-app-running.png)
*Frontend-додаток (React) успішно запущено на `localhost:3000` і взаємодіє з бекендом (Node.js).*
</details>

<details>
<summary>Frontend-backend interaction</summary>
![Browser Network Tab](docs/images/stage-0-network-requests.png)
*Вкладка "Мережа" в інструментах розробника браузера показує успішні HTTP-запити з фронтенду на бекенд-API.*
</details>

---

## 🛣 Roadmap
Етап 1: CI/CD Pipeline

Налаштування GitHub Actions workflows

Автоматична збірка та тестування

Створення Docker образів

Пуш образів у DockerHub

Етап 2: Infrastructure as Code

Створення VPC, EC2, S3 за допомогою Terraform

Налаштування безпеки (Security Groups, IAM)

Етап 3: Containerization

Dockerization бекенду та фронтенду

Docker Compose для локального розгортання

Етап 4: Kubernetes Deployment

Створення Kubernetes маніфестів

Налаштування Ingress, Services, Deployments

Етап 5: Monitoring

Налаштування Prometheus для збору метрик

Візуалізація в Grafana

---

## 📄 Ліцензія
Цей проект ліцензований за умовами MIT License. Див. файл [LICENSE](LICENSE) для деталей.

---

## 🤝 Внесок
Внески вітаються! Будь ласка, не соромтеся створювати issues або pull requests для будь-яких покращень.

---

## ⭐️ Якщо вам сподобався цей проект, будь ласка, поставьте зірочку на GitHub!
