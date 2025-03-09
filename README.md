# Automated Container Deployment and Administration in the Cloud

## Overview

The automation process includes provisioning the infrastructure using **Terraform** to create a server instance and cloud service. Then, **Ansible** is used to install Docker for setting up the server environment. Next, a **Dockerfile** is written to build the image and deploy the container to the server. All the code is pushed to the **GitHub repository**, and automation is implemented for **CI/CD** using a pipeline to build and deploy the application automatically using **GitHub Actions**.

---

## Prerequisites

To ensure smooth implementation, the following tools and accounts are required:

1. **Microsoft Azure Account**: An active Azure subscription and permissions are required to create resources.
2. **Azure CLI**: Install Azure CLI in Ubuntu using:
   
   sudo apt install azure-cli
   
   **Verify the installation**:
   az --version
   
   **Authenticate using**:
   az login

# Infrastructure Setup Using Terraform

This guide outlines the steps to automate the provisioning of cloud infrastructure on Azure using Terraform. The setup includes configuring Virtual Machines (VMs), networks, security groups, and other essential components.

---

## Prerequisites

- **Azure Account**: Ensure you have an active Azure subscription.
- **Terraform Installed**: Install Terraform using the following commands:
  sudo apt-get install terraform

  **Verify the installation**:
  terraform version

  **Enable AutoComplete**:
  terraform-install-autocomplete
  
 ## Steps to setup Terraform
Follow the steps below to install Terraform and verify the installation.

---

1. **Install Terraform**  
   Use the following command to install Terraform on your system:
   sudo apt-get install terraform

2. **Verify the installation**:
   terraform version

3. **Enable AutoComplete**:
   terraform-install-autocomplete

# Configuration Management Using Ansible

To automate the configuration of the server and to run the Dockerized "Hello World" application, Ansible is used. Ansible employs human-readable YAML language to define automation tasks. 
Below are the main steps to achieve this:

---

## Steps to Configure Using Ansible

### 1. Install Ansible

**Install Ansible**:   
sudo apt install ansible

**Verify the Installation**:
ansible --version

# Docker Container Deployment

The Ansible playbook installs Docker on the target server to automate the deployment of a sample web application, "Hello World." To deploy this application, both a `Dockerfile` and an `index.html` file are required. These files are used to containerize and run the application. Below are the details of the process:

---

## Files Required

1. **Dockerfile**:  
   This file defines the steps to build the Docker image. It uses the `nginx:alpine` base image, copies the `index.html` file into the container, and exposes port 80 for HTTP communication.

2. **index.html**:  
   This file contains the content of the "Hello World" web application, which will be served by the Nginx web server inside the container.

---

## Dockerfile Configuration

The `Dockerfile` uses the `nginx:alpine` base image and performs the following steps:

1. **Base Image**:  
   Uses the lightweight `nginx:alpine` image as the base.

2. **Copy Application Files**:  
   Copies the `index.html` file into the container to ensure the application files are included.

3. **Expose Port**:  
   Exposes port 80, the default HTTP port, to allow the container to listen for incoming web requests.

 # CI/CD Pipeline Integration Using GitHub Actions

To automate the building and deployment of the Docker container to the cloud infrastructure (Azure VM), a CI/CD pipeline is implemented using **GitHub Actions**. This pipeline builds the Docker image and deploys it to the Azure VM whenever changes are pushed to the repository. Below are the details of the process:

---

## Prerequisites

1. **GitHub Repository**:  
   A GitHub repository is required to host the code and trigger the CI/CD pipeline.

2. **Azure VM**:  
   An Azure VM is used as the deployment target. Ensure the VM is configured and accessible.

3. **GitHub Secrets**:  
   Store the following credentials in GitHub Secrets for secure access:
   - `VM_IP_ADDRESS`: Public IP address of the Azure VM.
   - `VM_USERNAME`: Username for the Azure VM.
   - `VM_PASSWORD`: Password for the Azure VM.

---

## GitHub Actions Workflow

The CI/CD pipeline is defined in a `deploy.yml` file located in the `.github/workflows/` directory of the repository. This workflow performs the following steps:

1. **Trigger**:  
   The workflow is triggered whenever code is pushed to the `main` branch.

2. **Environment**:  
   The workflow runs on the latest version of Ubuntu.

3. **Steps**:
   - Check out the repository code.
   - Build the Docker image.
   - Deploy the Docker container to the Azure VM using Ansible.

# Code Management Using GitHub

GitHub is a powerful platform for version control, collaboration, and project management. It is used to track and manage the project code. Below are the details of how GitHub is utilized for this project:

---

## GitHub Repository

A GitHub repository is created to store and manage the project code. The repository is made **public** for this project. The repository contains the following files:
- `main.tf`
- `playbook.yml`
- `Dockerfile`
- `index.html`
- `deploy.yml`

---

## Key Git Commands

The following Git commands are used to manage the code:

1. **Clone the Repository**:  
   Clone the repository to your local machine using the command:
   git clone your-repository url.git
   
2. **Add Changes**:
   git add .

3. **Commit Chnages**:
   git commit -m "My Deployment"

4. **Push Changes**:
   git push origin main      

   
 
