Deploy Cloud Native Monitoring Application on Kubernetes:
This project demonstrates how to build a Cloud-Native Resource Monitoring Application using Python & Flask, containerize it using Docker, 
push the image to AWS ECR, and deploy it on Kubernetes (AWS EKS) using Python automation.

What This Project Covers:
Creating a Python Monitoring Application using Flask from scratch
Running the Python application locally on port 5000
Containerizing the application using Docker
Writing a Dockerfile
Building a Docker image from Dockerfile
Running a Docker container from the image
Creating an AWS ECR repository and pushing the Docker image
Creating an AWS EKS cluster and worker nodes
Creating Kubernetes Deployment and Service using Python
Exposing the Kubernetes application using port forwarding

Technologies Used:
Python
Flask
psutil
Docker
AWS ECR
AWS EKS
Kubernetes
boto3
Kubernetes Python Client
kubectl

Prerequisites:
Make sure you have the following before starting:
AWS Account
AWS CLI configured with programmatic access
Python 3 installed
Docker installed and running
kubectl installed
VS Code or any code editor

Project Architecture:
User → Browser
        ↓
Kubernetes Service (EKS)
        ↓
Flask Application (Docker Container)
        ↓
AWS ECR (Docker Image)

Project Implementation:
Step1- Create Python Monitoring Application Using Flask
Build a Flask-based application to monitor system resources using psutil.
The application runs on port 5000.

step-2 Run Python Application Locally
pip3 install -r requirements.txt
python3 app.py
Access the application:
http://localhost:5000

step-3 Containerize the Application Using Docker
Create a Dockerfile to containerize the Flask application.

step-4 Write Dockerfile
FROM python:3.9-slim-buster
WORKDIR /app
COPY requirements.txt .
RUN pip3 install --no-cache-dir -r requirements.txt
COPY . .
ENV FLASK_RUN_HOST=0.0.0.0
EXPOSE 5000
CMD ["flask", "run"]

step-5 Build Docker Image
docker build -t cloud-native-monitoring-app .

step-6 Run Docker Container
docker run -p 5000:5000 cloud-native-monitoring-app

step-7 Push Docker Image to AWS ECR
Create an ECR repository
Authenticate Docker with ECR
Push the Docker image
docker tag cloud-native-monitoring-app:latest <ecr_repo_uri>:latest
docker push <ecr_repo_uri>:latest

step-8 Create AWS EKS Cluster and Node Group
Create an EKS cluster
Add worker node group
Configure kubectl for the cluster

step-9 Create Kubernetes Deployment and Service Using Python
Use Kubernetes Python client
Create Deployment and Service programmatically
Update the image URI with your ECR image
Run:
python3 eks.py

Verify Kubernetes Resources
kubectl get deployments
kubectl get services
kubectl get pods

step-10 Port Forward and Expose Application
kubectl port-forward service/<service-name> 5000:5000

Access the application:
http://localhost:5000

Outcome:
By completing this project, you will gain hands-on experience in:
Cloud-Native application development
Docker & Kubernetes
AWS ECR & EKS
Infrastructure automation using Python
