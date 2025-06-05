# 🚀 Jenkins CI/CD Pipeline with Terraform, Docker, SonarQube, Trivy & Kubernetes on AWS | Swiggy Clone

This project demonstrates a full end-to-end DevOps workflow for deploying a **Swiggy Clone Application** using modern CI/CD practices. The stack includes infrastructure provisioning with **Terraform**, CI/CD automation using **Jenkins**, static code analysis with **SonarQube**, container image vulnerability scanning with **Trivy**, containerization with **Docker**, and container orchestration using **Kubernetes** (deployed on **Amazon EKS**).

---
## Pipeline Structure & Final Build Result 

<img width="1440" alt="Screenshot 2025-06-03 at 6 23 00 PM" src="https://github.com/user-attachments/assets/126abb76-1f6b-4925-a39f-ce06ef9f3d04" />




## 📌 Key Features

- Provision AWS EC2 instances for Jenkins, SonarQube, and Docker using Terraform  
- Configure Jenkins for CI/CD automation  
- Integrate SonarQube for static code quality analysis  
- Scan Docker images for vulnerabilities using Trivy  
- Build and push Docker images to DockerHub  
- Create and configure an Amazon EKS Kubernetes cluster  
- Automate application deployment to EKS via Jenkins pipeline  
- Set up GitHub webhook to trigger CI/CD pipeline on code commits  

---

## 🛠️ Tech Stack

| Technology     | Purpose                                   |
|----------------|-------------------------------------------|
| Terraform      | Infrastructure provisioning (EC2, EKS)    |
| Jenkins        | CI/CD automation server                    |
| SonarQube      | Static code analysis and quality checks   |
| Trivy          | Container image vulnerability scanning    |
| Docker         | Containerization                           |
| DockerHub      | Container image registry                   |
| Kubernetes     | Container orchestration                     |
| AWS EKS        | Managed Kubernetes cluster on AWS cloud    |

---

## ⚙️ Pipeline Workflow

1. **Terraform** provisions EC2 instances to host Jenkins, SonarQube, and Docker  
2. **Jenkins** is installed and configured with required plugins  
3. **SonarQube** is integrated with Jenkins for static code analysis  
4. Jenkins pipeline performs:  
   - Code checkout from GitHub  
   - SonarQube analysis  
   - Trivy vulnerability scan on Docker image  
   - Build and push Docker image to DockerHub  
5. AWS **EKS** cluster is created and configured  
6. Jenkins deploys the application to the EKS Kubernetes cluster  
7. GitHub webhook triggers the pipeline automatically on code commits  

---

## 📌 Setup Instructions

### 1. Terraform Initialization

```bash
terraform init
terraform apply -auto-approve

```

### 2. Configure Jenkins

- Install Jenkins on the provisioned EC2 instance  
- Install required plugins:  
  - GitHub  
  - Docker Pipeline  
  - Kubernetes CLI  
  - SonarQube Scanner  
  - Trivy Scanner integration (if applicable)  
- Add necessary credentials in Jenkins:  
  - DockerHub credentials  
  - GitHub personal access token or SSH key  

---

### 3. Set up SonarQube

- Install SonarQube on EC2 or use a hosted instance  
- Start SonarQube server and create a project for the Swiggy Clone app  
- Generate an authentication token from SonarQube  
- Configure Jenkins to connect with SonarQube by adding the token under **Manage Jenkins > Configure System > SonarQube servers**

---

### 4. Create Jenkins Pipeline

- Create a `Jenkinsfile` in your repository with stages for:  
  - Code checkout  
  - SonarQube static code analysis  
  - Trivy vulnerability scanning of Docker images  
  - Docker image build  
  - Docker image push to DockerHub  
  - Deployment to Kubernetes cluster  
- Configure pipeline job in Jenkins to use this `Jenkinsfile`  

---

### 5. Create and Configure AWS EKS Cluster

- Create an EKS cluster using Terraform or AWS Console  
- Configure worker nodes and networking (VPC, subnets, security groups)  
- Download the `kubeconfig` file for your EKS cluster  
- Make sure Jenkins has access to this kubeconfig for deploying to the cluster  

---

### 6. Set up GitHub Webhook

- Go to your GitHub repository settings  
- Under **Webhooks**, add a new webhook with your Jenkins server URL and `/github-webhook/` endpoint  
- Set content type to `application/json`  
- Choose which events to trigger the webhook (usually **push** events) 
- Save the webhook to enable automatic pipeline triggers on code commits  



## Deployed Application

<img width="1440" alt="Screenshot 2025-06-05 at 10 59 13 AM" src="https://github.com/user-attachments/assets/fdb7809e-2719-4df3-80d7-a976d80b8998" />

 
