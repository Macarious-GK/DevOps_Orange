# Orange DevOps Internship Project

In my DevSecOps project at Orange Digital Hub. I specifically focuses on CI/CD for a Django application and MySQL server, ensuring seamless and automated deployment workflows, while also demonstrating the secure management of secret keys and tokens 🔑 HashiCorp Vault, showcasing real-life solutions for maintaining application security and operational efficiency. I focused on implementing GitOps with ArgoCD to automate Kubernetes deployments, integrating the ELK Stack (Elasticsearch, Logstash, Kibana) 📊 for real-time logging, utilizing Prometheus and Grafana for monitoring, employing Ansible for configuration management, and applying best security practices in Kubernetes such as RBAC, Network Policies, Persistent Volumes and CronJobs for app health. 

# Table of Contents

1. [Project Structure](#project-structure)
2. [DevSecOps SSDLC Integration](#devsecops-ssdlc-integration)
3. [Dockerization Best Practices](#dockerization-best-practices)
4. [Orchestration Using Kubernetes](#orchestration-using-kubernetes)
5. [Security Tools and Practices](#security-tools-and-practices)
6. [Infrastructure as Code (IaC) Tools](#infrastructure-as-code-iac-tools)
7. [GitOps with ArgoCD](#gitops-with-argocd)
8. [Monitoring](#monitoring-system)
8. [Logging with ELK-Stack](#logging-with-elk-stack)


---
![devsecops](/Figures/devsecops.png)
## Project Structure

### Application and Deployment
- **Dockerization & Orchestration**
  - [`Docker`](./Docker)
  - [`K8s`](./K8s)

### CI/CD Management
- **Jenkins - CI/CD & Argo - CD**
  - [`Jenkins`](./Jenkins)
  - [`ArgoCD`](./ArgoCD)

### Infrastructure as Code (IaC)
- **Provisioning & Configuration**
  - [`Terraform`](./Terraform)
  - [`Vagrant`](./Vagrant)
  - [`Ansible`](./Ansible)

### Secret Management
- [`Vault`](./Vault)

### Monitoring & Logging
- [`Grafana`](./Monitoring/Grafana)
- [`Prometheus`](./Monitoring/Prometheus)
- [`ELK-Stack`](./ELK)


## DevSecOps SSDLC Integration

- DevSecOps integrates SSDLC principles by adopting the "shift-left" strategy, embedding security testing early into the development lifecycle. 
- This proactive approach aims to identify and mitigate vulnerabilities before they are deployed to production.



## Dockerization Best Practices

- **Multi-stage Dockerfile**: This method reduces Docker image size and enhances security by using multiple build stages, ensuring only necessary dependencies are included in the final image.
- **Docker Compose**: Facilitates the management and orchestration of multi-container Docker applications, improving consistency across development and production environments.

---

## Orchestration Using Kubernetes

- **AWS EKS**: Amazon's managed Kubernetes service is used for deploying and managing containerized applications at scale in the cloud.
- **Minikube**: A tool that enables the local deployment of Kubernetes clusters, useful for testing and development in an on-premises environment.

### Kubernetes Security Best Practices
- **Persistent Volumes**: Ensures data durability and high availability in Kubernetes clusters.
- **Network Policies**: Control traffic flow and enforce security between pods to prevent unauthorized communication.
- **Role-Based Access Control (RBAC)**: Enforces least-privilege access by managing who can perform actions on resources within Kubernetes.
- **CronJob Checker Pods**: Ensures the reliability of scheduled tasks by monitoring the execution of cron jobs.
- **Secrets Management**: Safely stores and manages sensitive data like API keys, passwords, and certificates in Kubernetes clusters.

---

## Security Tools and Practices

### Security Testing in the DevSecOps Pipeline:
- **Code Linting**: Ensuring code quality and compliance with coding standards..
- **Static Application Security Testing (SAST)**: Identifying security flaws in the code.
- **Unit Testing**: Verifies the correctness of the application.
- **Docker Image Scanning**: Detects vulnerabilities within container images.

### Access Control
- **RBAC (Role-Based Access Control)**: Ensures users have only the necessary permissions.
- **Least Privilege**: Limits access rights for users, accounts, and computing processes to the minimum necessary.

### Credentials Management
- **Vault Server**: Secure storage and management of secrets such as API keys, passwords, and certificates.
- **Kubernetes Secrets and RBAC**: Manages sensitive data and enforces secure access controls within Kubernetes.
- **Jenkins Credential Management**: Secures sensitive data in Jenkins, including credentials for interacting with cloud platforms and other tools.

---

## Infrastructure as Code (IaC) Tools

- **Ansible**: Automation tool for `configuration management` and orchestration of infrastructure tasks.
- **Vagrant**: Tool for building and managing virtualized development environments for `on-premises provisioning`.
- **Terraform**: `Infrastructure provisioning` tool that allows for the creation, management, and versioning of infrastructure using code.

---

## GitOps with ArgoCD

- **`GitOps`**: The practice of managing infrastructure and applications using Git repositories as the source of truth for deployments. 
- **`ArgoCD`**: ArgoCD is a continuous delivery tool for Kubernetes that implements GitOps principles. It automates the deployment and synchronization of Kubernetes applications from Git repositories. Key features of ArgoCD include:
  - **Declarative Configuration**: Kubernetes resources are defined in Git and applied automatically.
  - **Syncing & Automation**: ArgoCD continuously monitors and syncs your applications with Git changes.
  - **Rollbacks**: ArgoCD allows easy rollbacks by reverting Git changes.

## Monitoring system

- **`Prometheus`**: An open-source monitoring system and time-series database for collecting metrics from applications and infrastructure.
- **`Alert Manager`**: A tool for handling alerts from Prometheus and routing them to the appropriate channels.
- **`Grafana`**: A visualization tool that integrates with Prometheus for creating dashboards and displaying metrics for monitoring application and infrastructure performance.

## Logging with ELK Stack
The logging process for a Django application using the **`ELK Stack`** involves seamlessly integrating **`Elasticsearch`**, **`Logstash`**, and **`Kibana`** to collect, process, and visualize logs.

1. **Django Application**: Logs are generated in JSON format and sent to **Logstash** through TCP.
2. **Logstash**: Acts as a log pipeline, ingesting the logs, processing them, and forwarding them to **Elasticsearch** for storage.
3. **Elasticsearch**: Efficiently stores and indexes the logs in time-based patterns, allowing fast querying.
4. **Kibana**: Provides an intuitive interface to visualize the logs, create dashboards, and monitor real-time application performance.
