# 🚀 **ArgoCD: The Heart of GitOps**

![ArgoCD Logo](/Figures/ArgoCD_logo.png)

ArgoCD is your **ultimate GitOps companion**, automating Continuous Delivery (CD) and ensuring that your Kubernetes cluster always reflects the **desired state** defined in your Git repository.  

### 🔑 **Why ArgoCD?**
- **Automated synchronization** with your Git repository for seamless deployments using webhooks.
- A **pull-based deployment model** ensures tighter security and fewer permissions.
- Acts as a **single source of truth**, providing easy management and consistent configuration.
- Effortless **rollback** capabilities for quick recovery.

#### ArgoCD takes your CD game to the next level—secure, streamlined, and always in sync.

![ArgoCD Workflow](/Figures/ArgoCD_Working.png)

---

### 🔧 **Steps to Get Started**

#### 1️⃣ Install ArgoCD in a Kubernetes Cluster & Access It

```bash
# Create a namespace for ArgoCD
kubectl create namespace argocd

# Install ArgoCD
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Access the ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# Login to ArgoCD using the admin user and initial token
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo
```

#### 2️⃣ Configure ArgoCD Application
Define the application source, destination, and sync policy in the ArgoCD_Application.yaml file.
Apply the configuration to your cluster:
- Source: Specify the Git repository containing your application manifests.
- Destination: Define the Kubernetes cluster and namespace where the application will be deployed.
- Sync Policy: Set rules for automated synchronization, such as selfHeal and prune.

```bash
kubectl apply -f ArgoCD_Application.yaml

```