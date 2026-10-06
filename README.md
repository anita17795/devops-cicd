# End-to-End CI/CD Deployment of a Containerized Web Application

## 📌 Project Overview

This project demonstrates an end-to-end CI/CD pipeline for deploying a containerized web application on AWS EC2.

The application source code is maintained in GitHub. GitHub Actions automatically builds the Docker image, pushes it to Docker Hub, and deploys the latest image to an AWS EC2 server.

## 🏗️ Architecture

Developer
   ↓
GitHub
   ↓
GitHub Actions
   ↓
Docker Build
   ↓
Docker Hub
   ↓
SSH
   ↓
AWS EC2
   ↓
Docker Container
   ↓
Nginx
   ↓
Web Application

## 🛠️ Technologies Used

- Linux (Amazon Linux 2023)
- AWS EC2
- AWS Elastic IP
- Git
- GitHub
- GitHub Actions
- Docker
- Docker Hub
- Nginx
- YAML
- SSH

## 🔄 CI/CD Workflow

1. Developer makes changes to the application.
2. Code is pushed to the `main` branch on GitHub.
3. GitHub Actions automatically starts the workflow.
4. Repository code is checked out onto the GitHub Actions runner.
5. Docker image is built using the Dockerfile.
6. GitHub Actions authenticates with Docker Hub using GitHub Secrets.
7. Docker image is pushed to Docker Hub.
8. GitHub Actions connects to the AWS EC2 server using SSH.
9. EC2 pulls the latest Docker image.
10. The existing container is stopped and removed.
11. A new container is started with the latest image.
12. The updated application becomes available through the EC2 Elastic IP.

## 🐳 Docker

The application uses Nginx as the web server.

The Dockerfile:

- Uses the lightweight `nginx:alpine` image.
- Copies the application HTML file into the Nginx web directory.
- Exposes port 80.

## 🔐 Security

Sensitive credentials are not stored directly in the workflow file.

GitHub Secrets are used for:

- Docker Hub username
- Docker Hub access token
- EC2 host
- EC2 username
- EC2 private SSH key

## 🚀 Deployment

The deployment is triggered automatically whenever code is pushed to the `main` branch.

Example:

```text
Code Change
     ↓
Git Push
     ↓
GitHub Actions
     ↓
Docker Build
     ↓
Docker Hub
     ↓
EC2 Deployment
     ↓
Updated Website
