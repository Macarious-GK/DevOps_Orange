# Vagrant Setup for Ansible Control and Managed Nodes  

This configuration defines a **Vagrant environment** consisting of one **Ansible Control Node** and two **Managed Nodes**. It uses Ubuntu 22.04 (`ubuntu/jammy64`) for all nodes.  

---
## Nodes Summary  

| **Node Name**       | **IP Address**    | **Memory** | **CPUs** | **VM Name**            | **Purpose**              |  
|----------------------|------------------|------------|----------|------------------------|--------------------------|  
| `control`           | `192.168.1.200`  | 4096 MB    | 3       | `Jenkins&Ansible_Control_VM`   | Ansible Control Node     |  
| `managed`           | `192.168.1.201`  | 4096 MB    | 3        | `Ansible_Managed_VM`   | Managed Node (Target 1)  |  
| `managed2`          | `192.168.1.202`  | 1024 MB     | 2       | `Ansible_Managed2_VM`  | Managed Node (Target 2)  |  

---

## Provisioning Details  

### Ansible Control Node  
- Installs **Ansible** for managing the target nodes.  
- Updates and upgrades the operating system.  
- Installs `curl` for additional operations.

### Managed Nodes  
- Updates and upgrades the operating system to ensure the latest packages are installed.  
