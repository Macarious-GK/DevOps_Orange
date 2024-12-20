# Jenkins Pipelines

This repository contains Jenkins pipelines for different parts of the application and infrastructure management process. The pipelines utilize a shared library from the following repository: [Jenkins Shared Library](https://github.com/Macarious-GK/Jenkins-Shared-Library.git).

## Jenkins Shared Library

The pipelines in this repository make use of a shared library to promote reusable and modular pipeline steps. The shared library is hosted in the following GitHub repository: [Jenkins Shared Library](https://github.com/Macarious-GK/Jenkins-Shared-Library.git).

To use the shared library in your Jenkins pipeline, add the following configuration to your `Jenkinsfile`:

```groovy
@Library('Jenkins-Shared-Library') _
// Pipeline Code
```
## Jenkins Folder Structure
```plaintext
Jenkins/
|── App_Pipeline/
|── DB_Pipeline/
|── CD_Pipline/
|── Infra_Pipeline/
|   ├── Ansible/
|   └── Terraform/
└── Readme.md
```


## Pipeline Stages
Throughout all the pipelines, I maintained best practices in writing the stages.

1. **Reusable Code**
   - Utilized shared library functions effectively.

2. **Parameterized Configuration**
   - Enabled flexible inputs for inventory files, credentials, and playbooks.

3. **Post-Build Actions**
   - **Always**: Cleans up the workspace to maintain a clean build environment.
   - **On Success**: Sends an email with a success message.
   - **On Failure**: Sends an email with an error message.

## Jenkins Pipelines

**App_Pipeline**: Pipeline responsible for building, testing, and deploying the `Django Application` image.
- Checkout SCM Stage
- Dependencies check Stage
- Linter Stage
- SAST Stage
- App Unit Testing Stage
- Build Image 
- Scanning Image
- Login & Push Image
- ArgoCD Sync 
- Notify pipline status
- Post Actions & cleanup Stage
---
  ![Prometheus](/Figures/Promethues_working.png)
---
**DB_Pipeline**: Pipeline responsible for building, testing, and deploying the `MYSQL Database` image. 
- This Pipline is show case for using **`Hashicorp Vault secret management`** tool. 
  - Checkout SCM Stage
  - Build Image 
  - Scanning Image
  - Login & Push Image
  - Notify pipline status
  - Post Actions & cleanup Stage
---
  ![Prometheus](/Figures/DB_Pipline.PNG)
---
**CD_Deployment**: Pipeline responsible for deploy our application on Local Cluster `Minikube`, Cloud Cluster `EKS AWS` and Docker-compose.
- Checkout SCM Stag
- Test SSH Access VMs
- Deployment on Minikube VM 1
- Deployment on Docker VM 2
- Deployment on AWS
- Notify pipline status
- Post Actions & cleanup Stage
---
  ![Prometheus](/Figures/CD_pipeline.png)
---
**Infra_Pipeline**/**Ansible**: It is responsible for creating `On Primise infrastructure` resources and install requeired dependences.
- This Pipline is show case for using **`Ansible`** tool. 
- Checkout SCM Stage
- Environment Check
- Test: Ping Machines
- TInstall Minikube & Kubernetes on Machine 1
- Install Docker on Machine 2
- Notify pipline status
- Post Actions & cleanup Stage
---
  ![Prometheus](/Figures/Infra_ansible_pipline.PNG)
---
**Infra_Pipeline**/**Terraform**: It is responsible for both **applying** and **destroying** `AWS Cloud infrastructure` resources by using **Build with Parameters** action: (apply or destroy)
- Checkout SCM Stage
- IaS Scanning
- Initialize Terraform Stage
- Terraform Validate Stage
- Terraform Plan Stage
- Terraform Apply/Destroy Stage
- Notify pipline status
- Post Actions & cleanup Stage
---
  ![Prometheus](/Figures/Infra_terra_pipline.PNG)
---
## Plugin Installation

### Required Plugins
1. **AWS Credentials Plugin**: For managing AWS credentials in Jenkins.
2. **GitHub Plugin**: For integrating Jenkins with GitHub repositories.
3. **Ansible Plugin**: For executing Ansible playbooks directly from Jenkins.
4. **SSH Agent Plugin**: For securely managing SSH keys within Jenkins pipelines.
5. **Mailer Plugin**: For configuring and sending email notifications from Jenkins.

#### Install Plugins
1. Go to **Manage Jenkins** -> **Manage Plugins**.
2. Select the plugins and click **Install without Restart**.
## Setup WebHook

### Configure WebHook in GitHub:
1. Go to your GitHub repository's **Settings** -> **Webhooks** -> **Add Webhook**.
2. Set the "Payload URL" to `http://your-jenkins-server/github-webhook/`.
3. Set content type to `application/json`.
4. Choose **Just the push event** and click **Add Webhook**.

### Enable WebHook in Jenkins:
1. In your Jenkins job, under **Build Triggers**, select **GitHub hook trigger for GITScm polling**.
2. Ensure Jenkins is configured with the GitHub plugin to receive webhooks.


## How to Run the Pipelines
1. Configure Jenkins Shared Library under **Manage Jenkins** -> **Configure System** -> **Global Pipeline Libraries**.
2. Update your `Jenkinsfile` to use the shared library.
3. Trigger pipelines through Jenkins UI or set automated SCM-based triggers.


