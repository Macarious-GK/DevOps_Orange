# ⚙️ Ansible For configureation management

- Ansible is an automation tool that helps you manage and configure servers, deploy applications, and automate tasks. It uses simple, readable files called playbooks to define the tasks. Ansible connects to remote machines via SSH to perform actions, without needing any extra software installed on them. It makes managing infrastructure easier and more consistent.

![Ansible Logo](/Figures/ansible_logo.png)

## Playbooks 

- Ping Test Playbook (ping_check.yml):
    - Verifies network connectivity to the target machines by using a simple ping test.
- Install Docker Playbook (install_docker.yml):
    - Installs Docker on the target machines, including necessary dependencies and configurations.
- Run Docker Image Playbook (Pull&Run_dockerImage_Playbook.yml):
    - Pulls and runs a specified Docker image on the target machines.
- Install Minikube & kubectl Playbook (Install_minikube&kubectl.yml):
    - Installs minikube and kubectl on the target machines, including necessary dependencies and configurations.
---

## Usage  Notes

1. **Target Machines**:
   - Ensure target machines are accessible via SSH.
   - Verify the Ansible Control Node can connect to the target machines.

2. **Project Structure**:
   - `Ansible/` directory contains:
     - Playbooks (`Playbooks/`)
     - Inventory files (`Inventory/`)

---

## Files

| Files                        | Description                                  |
|------------------------------|----------------------------------------------|
| `Playbooks/ping_check.yml`   | Path to the Ansible test playbook.               |
| `Playbooks/install_docker.yml`  | Path to the Ansible Docker Installation playbook.       |
| `Playbooks/Install_minikube&kubectl.yml`  | Path to the Ansible Minikube & kubectl Installation playbook.       |
| `Playbooks/Pull&Run_dockerImage_Playbook.yml`  | Path to the Ansible Docker Pull and Run playbook.       |
| `Inventory/inventory.ini`    | Path to the inventory file for Machine 1.   |
| `Inventory/inventory_2.ini`  | Path to the inventory file for Machine 2.   |

---

