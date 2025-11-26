Smart Inventory Management System (SIMS)

Smart Inventory Management System (SIMS) is a cloud-ready, production-grade inventory management application built using Python and Flask. The system is fully containerized using Docker, automated through CI/CD pipelines, and deployed on Amazon EKS using Kubernetes. Terraform is used to provision infrastructure, and monitoring is implemented through CloudWatch, Prometheus, and Grafana.

Project Overview

This project demonstrates the end-to-end DevOps lifecycle of a real-world application. It includes application development, Docker-based containerization, Kubernetes deployments, continuous integration and delivery using Jenkins, infrastructure automation using Terraform, and observability using monitoring tools.

Objective

To design and deploy an inventory management system capable of handling multi-warehouse inventory, CRUD operations, containerized workloads, automated pipelines, scalable Kubernetes deployments, and fully automated infrastructure provisioning. The system is intended to meet production-level requirements such as reliability, scalability, monitoring, and smooth release management.

Key Features

Python Flask web application for inventory CRUD operations

Containerized application using Docker

Kubernetes-based deployment on Amazon EKS

Jenkins pipeline for continuous integration and delivery

Infrastructure provisioning using Terraform

Load balancing and autoscaling using AWS services

Real-time logging and monitoring using CloudWatch, Prometheus, and Grafana

Architecture Summary

The system consists of the following layers:

Application Layer: Flask-based web interface with inventory CRUD functions
Container Layer: Docker image for consistent application execution
Registry Layer: Amazon Elastic Container Registry for image storage
Orchestration Layer: Kubernetes deployment on AWS EKS
CI/CD Layer: Jenkins pipeline for automated build, test, image push, and deployment
Infrastructure Layer: Terraform modules for VPC, EKS, IAM, networking
Monitoring Layer: Prometheus metrics, Grafana dashboards, CloudWatch logs

Repository Structure

Smart-Inventory-Management-System
app/
Dockerfile
Jenkinsfile
k8s/
terraform/
docs/
README.md

Phase 1: Development

The application was developed using the Flask framework with Jinja2-based HTML templates. The development workflow includes virtual environments, dependency installations, and local testing.

Local Setup Commands
cd app
python3 -m venv venv
source venv/bin/activate (Windows: venv\Scripts\activate)
pip install -r requirements.txt
python main.py

Docker Build and Run
docker build -t sims-dev .
docker run -p 5000:5000 sims-dev

Phase 2: Staging (CI/CD and Infrastructure)

Continuous Integration and Delivery is implemented using Jenkins. The staging environment mirrors production and is used for testing images, deployments, and Kubernetes manifests.

Jenkins Pipeline Stages

Clone Git repository

Build Docker image

Push image to Amazon ECR

Deploy to EKS using kubectl

Terraform is used to automatically provision AWS resources. It generates the VPC, subnets, NAT gateways, IAM roles, EKS control plane, and node groups.

Terraform Commands
terraform init
terraform apply

Phase 3: Production Deployment

The production environment includes:

Multiple replica deployments for high availability

Horizontal Pod Autoscaling

ALB Ingress Controller for load balancing

Blue-Green deployment strategy using Kubernetes and Jenkins

Centralized logging through CloudWatch

Metrics collection with Prometheus and visualization with Grafana

Example Kubernetes Deployment (Production)

apiVersion: apps/v1
kind: Deployment
metadata:
name: sims-prod
spec:
replicas: 3
selector:
matchLabels:
app: sims
template:
metadata:
labels:
app: sims
spec:
containers:
- name: sims-app
image: <ecr-repo>:prod
ports:
- containerPort: 5000

Outcomes

End-to-end DevOps pipeline successfully implemented

Fully automated infrastructure using Terraform

Reliable and scalable Kubernetes deployment on EKS

Effective monitoring and observability setup

Demonstrated real-world CI/CD, IaC, Kubernetes, AWS, and containerization concepts in one project

Tech Stack Summary

Application: Python, Flask, HTML, Jinja2
Containers: Docker
Registry: Amazon ECR
Orchestration: Kubernetes (Amazon EKS)
CI/CD: Jenkins
Infrastructure as Code: Terraform
Monitoring: Prometheus, Grafana, CloudWatch
Cloud Platform: AWS

Closing Statement

Smart Inventory Management System (SIMS) showcases a complete DevOps workflow including development, containerization, continuous delivery, Kubernetes orchestration, infrastructure automation, and monitoring. It is a strong portfolio project demonstrating practical cloud and DevOps proficiency.
