# GitOps & DevOps: From Code to Kubernetes on macOS

[![CI Pipeline Status](https://github.com/cicero-w/devops-portfolio-project/actions/workflows/ci.yml/badge.svg)](https://github.com/cicero-w/devops-portfolio-project/actions/workflows/ci.yml)
[![Docker Image Version (Backend)](https://img.shields.io/docker/v/cicero2/devops-portfolio-backend?label=backend&logo=docker&sort=latest)](https://hub.docker.com/r/cicero2/devops-portfolio-backend)
[![Docker Image Version (Frontend)](https://img.shields.io/docker/v/cicero2/devops-portfolio-frontend?label=frontend&logo=docker&sort=latest)](https://hub.docker.com/r/cicero2/devops-portfolio-frontend)
[![GitHub license](https://img.shields.io/github/license/cicero-w/devops-portfolio-project)](https://github.com/cicero-w/devops-portfolio-project/blob/master/LICENSE)

**Complete implementation of a DevOps pipeline for a web application using modern practices: CI/CD, Infrastructure as Code, Kubernetes, and GitOps, tailored for a local development environment.**

## Project overview

This project demonstrates the full deployment cycle of a cloud-native application (Todo App) using a modern DevOps stack. The goal is to create a reliable, automated, and secure pipeline from code to production without relying on paid cloud services. This setup is perfect for local development and portfolio demonstration on a macOS environment.

**Author:** Pavlo \
**Contacts:** [paul.antonenko.w@gmail.com](paul.antonenko.w@gmail.com) | [LinkedIn](https://www.linkedin.com/in/pavlo-antonenko/) \
**Live Demo:** http://your-ip

---

## System Architecture

_The architecture is designed to be self-contained and free, leveraging local virtualization and containerization tools on macOS._

### Components:
1. **Source code:** GitHub repository with branching using the GitFlow strategy
2. **CI/CD:** GitHub Actions for building, testing, and scanning images
3. **Image registry:** DockerHub
4. **Local Infrastructure:** Linux VM on UTM + Docker Desktop for Mac
5. **Infrastructure as Code:** Ansible for VM provisioning automation
5. **Containerization:** Docker with multi-stage builds
6. **Orchestration:** Kubernetes (Docker Desktop built-in)
6. **GitOps:** ArgoCD for automated deployments
7. **Monitoring:** Prometheus/Grafana stack

---

## Technology Stack

| Category | Technologies |
|-----------|------------|
| **Local Environment** | macOS, UTM (Ubuntu Server VM) |
| **Infrastructure as Code** | Ansible |
| **CI/CD** | GitHub Actions |
| **Containers** | Docker, Docker Compose |
| **Orchestration & GitOps** | Kubernetes (Docker Desktop), Helm, ArgoCD |
| **Web Servers** | Nginx (Reverse Proxy) |
| **Programming** | Node.js (Express), React (Vite) |
| **Database** | SQLite |
| **Version Control** | Git, GitHub |
| **Image Registry** | DockerHub |

---

## Repository Structure

<pre>
devops-portfolio-project/
├── infrastructure/
│   
├── .github/
│   └──workflows/
│       └── ci.yml                  # CI/CD Pipeline
├── app/
│   ├── backend/                    # Node.js API server
│   │   ├── src/
│   │   │   ├── persistence/        # Database layer
│   │   │   ├── routes/             # API endpoints
│   │   │   └── index.js            # Main server file
│   │   ├── Dockerfile              # Multi-stage production build
│   │   ├── healthcheck.js
│   │   ├── package.json
│   │   └── package-lock.json
│   └── frontend/                   # React client
│       ├── src/
│       │   ├── components/
│       │   ├── App.jsx
│       │   └── main.jsx
│       ├── Dockerfile              # Multi-stage with Nginx
│       ├── nginx.conf              # Custom Nginx configuration
│       ├── package.json
│       ├── package-lock.json
│       └── vite.config.js
├── nginx/                          # Reverse proxy configuration
│   ├── nginx.conf
│   └── default.conf
├── docker-compose.yml              # Multi-container orchestration
├── .dockerignore
├── .gitignore
├── LICENSE
└── README.md
</pre>

---

## Current Status

### Stage 0: Preparation ✅ (Completed)
- [x] Created public GitHub repository
- [x] Initialized folder structure
- [x] Added base application code (Node.js backend + React frontend)
- [x] Configured `master` branch

### Stage 1: Manual VM Setup and Docker Deployment ✅ (Completed)
- [x] VM Configuration: Set up Ubuntu Server VM in UTM with bridged networking
- [x] SSH Access: Configured passwordless SSH connection from macOS to VM
- [x] Docker Installation: Installed Docker and Docker Compose on VM
- [x] Application Containerization:
    + Created multi-stage Dockerfile for React frontend with Nginx
    + Optimized Node.js backend Dockerfile with security best practices
    + Implemented health checks for all services
- [x] Reverse Proxy Setup: Configured Nginx with:
    + Load balancing upstream configuration
    + Security headers and rate limiting
    + JSON logging for monitoring integration
    + Gzip compression optimization
- [x] Multi-Container Architecture: Docker Compose setup with:
    + Isolated network with static IP assignment
    + Resource limits and reservations
    + Service dependencies and health checks
    + Volume management for persistent logs
- [x] Production Deployment: Successfully deployed full-stack application accessible via `http://vm-ip`

### Stage 2: Build and Security Automation (CI) ✅ (Completed)
- [x] DockerHub Integration: Created public repositories for backend and frontend
- [x] GitHub Secrets: Configured secure authentication with DockerHub tokens
- [x] GitHub Actions CI Pipeline:
    + Dockerfile Linting: Hadolint validation with industry best practices
    + Multi-stage Build Process: Optimized Docker image construction
    + Container Testing: Automated health check validation for both services
    + Security Vulnerability Scanning: Trivy integration with SARIF reporting
    + Automated Publishing: Docker images pushed to DockerHub registry
- [x] Security Integration:
    + SARIF reports uploaded to GitHub Security tab
    + Critical and high-severity vulnerability detection
    + Automated security scanning on every commit
- [x] CI/CD Workflow Features:
    + Parallel job execution for optimal performance
    + Artifact caching between pipeline stages
    + Conditional publishing (master/develop branches only)
    + Comprehensive job summaries and reporting

Key CI/CD Achievements:
  - Zero-touch deployment pipeline - from commit to registry automatically
  - Security-first approach - every image scanned before publication
  - Quality gates - Dockerfile linting and container testing mandatory
  - Audit trail - complete visibility of build and security scan results

### Next Steps:
- [ ] Stage 3: Infrastructure as Code with Ansible and Deployment Automation (CD)
- [ ] Stage 4: Kubernetes and GitOps with ArgoCD
- [ ] Stage 5: Monitoring and Observability

---

## CI/CD Pipeline Details

<details>
<summary>Automated Workflow Triggers:</summary>
  
- Push to master/develop: Full pipeline with publishing to DockerHub
- Pull Requests to master: Build, test, and scan without publishing
- Manual dispatch: Available for on-demand pipeline execution

</details>

<details>
<summary>Pipeline Stages:</summary>
  
1. Lint Dockerfiles
    + Hadolint validation for both frontend and backend
    + Industry best practices enforcement
    + Security and optimization rule checking

2. Build, Test, and Scan
    + Multi-stage Docker image construction
    + Container functionality testing
    + Trivy security vulnerability scanning
    + SARIF report generation for GitHub Security

3. Publish to Registry
    + Conditional publishing (master/develop only)
    + Multi-tag strategy (branch, SHA, latest)
    + DockerHub registry integration

</details>

<details>
<summary>Security Features:</summary>
  
- Vulnerability Scanning: Every image scanned for CVE database matches
- Security Reports: Automated upload to GitHub Security tab
- Risk Management: Known vulnerabilities documented and assessed for business impact
- Access Control: Token-based authentication with minimal permissions
- Audit Logging: Complete pipeline execution history

</details>

---

## Known Security Issues

This section demonstrates real-world vulnerability management practices as found in production environments.

<details>
<summary>Container Base Images</summary>

- libxml2 CVEs (High): Alpine Linux upstream vulnerabilities
  + Status: Monitoring for Alpine security updates
  + Impact: No direct application functionality affected
  + Mitigation: Network isolation, security headers, regular base image updates

</details>
<details>
<summary>Application Dependencies</summary>

- cross-spawn ReDoS (High): Regular expression denial of service potential
  + Status: Risk accepted - low exploitability in containerized environment
  + Mitigation: Resource limits, timeout configurations
- brace-expansion (Low): Minor dependency vulnerability
  + Status: Monitoring for package maintainer updates

</details>
<details>
<summary>Security Management Approach</summary>

- Continuous Monitoring: Automated scanning on every commit
- Risk Assessment: Business impact evaluation for each vulnerability
- Remediation Strategy: Prioritized by severity and exploitability
- Documentation: Complete audit trail in GitHub Security tab

</details>

_Note: In production environments, maintaining a vulnerability backlog with documented risk acceptance is standard practice. Not all CVEs require immediate remediation._

---

## How to Run Project Locally

The instructions below will allow you to run a copy of the project on your local computer for development and testing (Stage 0 setup).

### Prerequisites:

Before you start, make sure that your computer has:
*   **Node.js** (version 18 or higher) - runtime environment for JavaScript.
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
<summary>1. Clone the repository:</summary>
  
```bash
   git clone https://github.com/cicero-w/devops-portfolio-project.git
   cd your-repository
```
</details>
<details>
<summary>2. Start the backend (API server)</summary>

```bash
    cd app/backend
    npm install
    npm run dev
    # Server will be available at http://localhost:3000
```
</details>
<details>
<summary>3. Launch the frontend (client side):</summary>

```bash
    cd app/frontend
    npm install
    npm run dev
    # Application will be available at http://localhost:5173
```
</details>

---

## System Operation Screenshots

<details>
<summary>Stage 0: Local Development</summary>

![Local Application Running](docs/images/stage-0/app-running.png)
_Todo application running locally with Node.js backend and React frontend_

</details>
<details>
<summary>Stage 1: Production Deployment on VM</summary>

![Full-stack Application Running](docs/images/stage-1/app-running.png)
_Full-stack application deployed on Ubuntu VM with Docker containers_

![Services  Running](docs/images/stage-1/app-running-docker.png)
_All services running with health checks in Docker Compose_

</details>
<details>
<summary>Stage 2: CI/CD Pipeline</summary>

![GitHub Actions workflow](docs/images/stage-2/run-jobs.png)
_GitHub Actions workflow run showing all jobs (Lint, Build/Test/Scan, Publish) with green checkmarks_

![DockerHub repositories](docs/images/stage-2/images.png)
_DockerHub repositories showing published images with multiple tags (master, develop, SHA tags)_

![GitHub Security](docs/images/stage-2/code-scanning.png)
_GitHub Security tab displaying Trivy scan results with vulnerability reports for both containers_

</details>

---

## Roadmap

The following stages outline the path from a basic application to a fully automated DevOps pipeline.

* Stage 0: Preparation ✅
  + Create a public GitHub repository
  + Initialize the folder structure
  + Push the application's base code

* Stage 1: Manual Deployment on Local VM ✅
  + Set up a Linux VM using UTM on macOS
  + Manually configure the VM (install Docker, Git)
  + Clone the repository and run the application using Docker Compose
  + Configure Nginx reverse proxy with security headers
  + Implement health checks and monitoring readiness

* Stage 2: Build and Security Automation (CI) ✅
  + Set up DockerHub repositories
  + Configure GitHub Secrets for DockerHub credentials
  + Create a GitHub Actions workflow to lint, build, scan (with Trivy), and push Docker images to DockerHub
  + Implement automated security vulnerability scanning
  + Integrate quality gates and automated testing
 
* Stage 3: Infrastructure as Code (Ansible) and Deployment Automation (CD)
  + Write Ansible playbooks to automate the VM setup from Stage 1
  + Automate the deployment process on the VM using docker compose
  + Integrate this into the CI/CD pipeline
  + Implement infrastructure provisioning and configuration management
 
* Stage 4: Kubernetes and GitOps
  + Enable Kubernetes in Docker Desktop
  + Create Helm charts for the application
  + Set up ArgoCD to manage deployments from Git
  + Implement GitOps principles

* Stage 5: Monitoring and Logging
  + Deploy Prometheus/Grafana to the Kubernetes cluster.
  + Configure dashboards to monitor application metrics.
  + Implement centralized logging and alerting

---

## Production Deployment on VM

### Architecture Overview:

`Internet → VM (Ubuntu) → Nginx (Port 80) → Frontend (Port 3000) → Backend API (Port 8000)`

<details>
<summary>Deployment Process:</summary>
  
  - VM Setup: Ubuntu Server VM with 2+ CPU, 2-4GB RAM
  - Docker Installation: Latest Docker CE + Docker Compose
  - Application Build: Multi-stage Docker builds for optimized images
  - Service Orchestration: Docker Compose with health monitoring
  - Access: Application available at `http://vm-ip-address`
</details>
<details>
<summary>Key Features:</summary>
  
  - **High Availability:** Health checks with automatic container restart
  - **Security:** Non-root containers, security headers, rate limiting
  - **Performance:** Multi-stage builds, Nginx caching, resource limits
  - **Observability:** Structured JSON logging, health endpoints
  - **Scalability:** Load balancer configuration ready for horizontal scaling
</details>
<details>
<summary>Deployment Commands</summary>

  ## On VM (Ubuntu):

  ```bash
   # Update system and install Docker
  sudo apt update && sudo apt upgrade -y
  curl -fsSL https://get.docker.com -o get-docker.sh
  sudo sh get-docker.sh
  sudo usermod -aG docker $USER

  # Clone and deploy
  git clone https://github.com/cicero-w/devops-portfolio-project.git
  cd devops-portfolio-project
  docker compose up -d --build

  # Monitor deployment
  docker compose ps
  docker compose logs -f
  ```
</details>

---

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contribution
Contributions are welcome! Please feel free to submit issues and pull requests