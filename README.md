# Orange DevOps Internship Project

This project implements industry best practices in DevOps, leveraging a range of tools and technologies for cloud provisioning, security, containerization, orchestration, CI/CD, and monitoring. The following outlines the key components and practices used in the project.

## Project Structure

### Application and Deployment
- **Dockerization & Orchestration**
  - [`Docker`](./Docker)
  - [`K8s`](./K8s)

### CI/CD Management
- **CI - Jenkins & CD - ArgoCD**
  - [`Jenkins`](./Jenkins)
  - [`ArgoCD`](./ArgoCD)

### Infrastructure as Code (IaC)
- **Provisioning & Configuration**
  - [`Terraform`](./Terraform)
  - [`Vagrant`](./Vagrant)
  - [`Ansible`](./Ansible)

### Secret Management
- [`Vault`](./Vault)

### Monitoring
- [`Grafana`](./Monitoring/Grafana)
- [`Prometheus`](./Monitoring/Prometheus)

![devsecops](/Figures/devsecops.png)

---

## SSDLC Integration

The Jenkins pipelines integrate SSDLC principles by adopting the "shift-left" strategy, embedding security testing early into the development lifecycle. This proactive approach aims to identify and mitigate vulnerabilities before they are deployed to production.

Key security measures include:
- **Code Linting**: Ensuring code quality and compliance with coding standards.
- **Static Application Security Testing (SAST)**: Identifying security flaws in the code.
- **Docker Image Scanning**: Scanning images for vulnerabilities before deployment.

---

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
- **Linting**: Checks for syntax and coding errors.
- **SAST**: Analyzes the source code for vulnerabilities.
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

- **GitOps**: The practice of managing infrastructure and applications using Git repositories as the source of truth for deployments. `ArgoCD` is used to manage and sync Kubernetes applications declaratively from Git.

---

## Monitoring

- **`Prometheus`**: An open-source monitoring system and time-series database for collecting metrics from applications and infrastructure.
- **`Alert Manager`**: A tool for handling alerts from Prometheus and routing them to the appropriate channels.
- **`Grafana`**: A visualization tool that integrates with Prometheus for creating dashboards and displaying metrics for monitoring application and infrastructure performance.

---


<!-- # Orange DevOps Internship Project

This project follows best practices in DevOps implementation, incorporating various tools and technologies for cloud provisioning, security, containerization, orchestration, CI/CD, and monitoring.
## Project Folders
- APP
    - [`APP`](./APP)
- Dockerization & Orcheteration
    - [`Docker`](./Docker)
    - [`K8s`](./K8s)
- CI-Jenkins/CD-ArgoCD
    - [`Jenkins`](./Jenkins)
    - [`ArgoCD`](./ArgoCD)
- Infrastructure as Code
    - [`Terraform`](./Terraform)
    - [`Vagrant`](./Vagrant)
    - [`Ansible`](./Ansible)
- Secret Management
    - [`Vault`](./Vault)
- Monitoring
    - [`Monitoring`](./Monitoring)

![devsecops](/Figures/devsecops.png)



## SSDLC Integration
- The Jenkins pipelines incorporate SSDLC principles by applying the "shift-left" approach, which integrates security testing early in the development lifecycle. This proactive method helps address vulnerabilities before they reach production. 
- Key security measures include code linting, static application security testing, and Docker image scanning




## Dockerization Best Practices
- **Multi-stage Dockerfile**: Optimizing Docker images by using multiple stages to reduce image size and improve security.
- **Docker Compose**: Simplifying Docker deployment and managing multi-container applications.

## Orchestration Using Kubernetes
- **AWS EKS**: Cloud deployment using Amazon EKS for managing containerized applications.
- **Minikube**: Local Kubernetes deployment for on-premises development and testing.

### Security Best Practices in Kubernetes
- **Persistent Volumes**: Ensuring data persistence and high availability in Kubernetes clusters.
- **Network Policies**: Restricting and controlling network access between Kubernetes pods.
- **Roles and RoleBindings**: Managing access control using Kubernetes RBAC to enforce least privilege.
- **CronJob Checker Pods**: Monitoring and managing cron jobs in Kubernetes to ensure reliability.
- **Secrets Management**: Storing and securing sensitive information like passwords and API tokens in Kubernetes.

## Security Tools and Practices
- **Security testing** `DevSecOps Pipeline`:
    - Linting stage for code quality.
    - Static Application Security Testing (SAST) for identifying vulnerabilities.
    - Unit testing to ensure application stability.
    - Image scanning for vulnerabilities in container images.

- **Acces Control**
    - RBAC
    - Leastprevilag

- **Credentials**
    - **Vault Server**: Secure storage and access control for secrets and sensitive data.
    - **Kubernetes Secrets and RBAC**: Managing sensitive data and controlling access within Kubernetes clusters.
    - **Jenkins Credential Management**: Managing credentials in Jenkins for secure CI/CD pipelines.

## Infrastructure as Code (IaC) Tools
- **Ansible**: Configuration management for automating tasks and managing infrastructure.
- **Vagrant**: On-premises provisioning and environment management.
- **Terraform**: Cloud provisioning with best practices for infrastructure management.

## GitOps 
- **GitOps**: Managing deployments with GitOps principles, using ArgoCD to sync and manage Kubernetes applications declaratively.


## Monitoring
- **Prometheus**: Monitoring tool for collecting metrics from applications and infrastructure.
- **Alert Manager**: Managing and sending alerts based on Prometheus metrics.
- **Grafana**: Visualization tool for creating dashboards and monitoring the health and performance of applications and infrastructure.

 -->



<!-- ```cmd
Monitoring/
|── Prometheus/
|   ├── Docker/
|   └── K8s/
|   
|── Grafana/
|   ├── Docker/
|   |   └── dashboards/
|   └──K8s/
└── Readme.md
``` -->







<!-- | **Application and Deployment** | **CI/CD Management**    | **IaC**                     |  -->
<!-- |----------------------|------------------                 |------------                 |
| - [`Docker`](./Docker)         | - [`Jenkins`](./Jenkins)| - [`Terraform`](./Terraform)|   
|  - [`K8s`](./K8s)              | - [`ArgoCD`](./ArgoCD)  | - [`Vagrant`](./Vagrant)    |  
|                                |                         | - [`Ansible`](./Ansible)    | -->

<!-- [Heading IDs](#heading-ids)

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |

| Syntax | Description |
| --- | ---- |
| Header | Title |
| Paragraph | Text |
 -->
<!-- 
```cmd
DevOps-Monitoring/
├── Images/
|── Prometheus/
├   ├── Docker/
|   │   └── dashboards.yaml
|   |── K8s/
|   |   └── datasources.yaml
|   └── Linux/
|       |── prometheus.service
|       └── prometheus.yml   
└── Grafana/
    ├── Docker/
    │   └── dashboards.yaml
    └── K8s/
        └── datasources.yaml
``` -->

