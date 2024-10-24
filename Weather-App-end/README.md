# CloudWeatherOps

CloudWeatherOps is a scalable weather forecasting web application built using Java Spring Boot. This project demonstrates end-to-end DevOps practices including containerization with Docker, orchestration with Kubernetes, and deployment on AWS EKS. The application uses continuous integration (CI) and continuous delivery (CD) pipelines powered by GitHub Actions and GitOps (ArgoCD), and it leverages Helm charts for deployment flexibility and Ingress configuration for load balancing and DNS management.

---

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Setup Instructions](#setup-instructions)
  - [Prerequisites](#prerequisites)
  - [Local Setup](#local-setup)
  - [Deploying to Kubernetes](#deploying-to-kubernetes)
  - [CI/CD Setup](#ci-cd-setup)
- [AWS EKS Configuration](#aws-eks-configuration)
- [Helm Configuration](#helm-configuration)
- [Ingress Controller Setup](#ingress-controller-setup)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

CloudWeatherOps provides real-time weather information via a user-friendly web interface. The application is containerized and orchestrated using Kubernetes, deployed on AWS Elastic Kubernetes Service (EKS), and follows best practices for continuous integration and continuous delivery.

---

## Features

- **Weather Forecasting:** Displays real-time weather data.
- **Scalable:** Designed for horizontal scaling using Kubernetes.
- **Secure & Lightweight Docker Images:** Dockerized with a focus on reducing image size and enhancing security.
- **AWS EKS Deployment:** Deployed to AWS EKS with proper IAM policies and networking.
- **Helm Integration:** Simplified deployment using Helm charts.
- **CI/CD Pipelines:** Automated build and deployment using GitHub Actions and ArgoCD.
- **Load Balancing & DNS:** Managed by Ingress controller with AWS load balancer and DNS configuration.

---

## Architecture

```bash
┌──────────────┐     ┌──────────┐      ┌───────────────┐
│  React.js    │────▶│  Node.js │────▶│  Spring Boot  │
│  (Frontend)  │     │(API Gateway)│   │   (Backend)   │
└──────────────┘     └──────────┘      └───────────────┘
                        │                    │
                        ▼                    ▼
                    ┌────────┐           ┌────────┐
                    │MongoDB │◀────────▶│Weather  │
                    │        │  Forecast│  API    │
                    └────────┘           └────────┘
