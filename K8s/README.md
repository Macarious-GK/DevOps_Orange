# Deployment on Minikube
This guide explains how to deploy an application on Minikube using Kubernetes `kubectl`. It covers the creation of a namespace, setup of persistent storage, initialization of data, deployment of the Database & application.

  ![K8s](/Figures/Kubernetes_logo.png)

## 0. Run Minikube on the Calico Container Network Interface (CNI)
Calico is a popular CNI plugin for Kubernetes that provides networking and network policy capabilities
```bash
minikube --cni calico
```

## 1. Namespace Creation

To logically group all related Kubernetes resources, we first create a namespace. Namespaces help in organizing and isolating different components of the application.

### Steps:
1. Define a namespace in your Kubernetes configuration.
2. Apply the configuration to create the namespace:

    ```bash
    kubectl apply -f Namespace.yaml
    ```

## 2. Persistent Storage Setup

For managing Database storage, we set up a Persistent Volume (PV) and a Persistent Volume Claim (PVC). The PV provides a storage resource in the cluster, while the PVC allows the Database to request and use that storage.

### Definitions:
- **Persistent Volume (PV)**: Represents a piece of storage available for use.
- **Persistent Volume Claim (PVC)**: Requests storage from the available PV.

### Steps:
1. Define a Persistent Volume in your configuration.
2. Define a Persistent Volume Claim that requests storage from the PV.
3. Apply the configurations to create the PV and PVC:

    ```bash
    kubectl apply -f PV.yaml
    kubectl apply -f PVC.yaml
    ```

## 3. Role and RoleBinding Configuration

To grant the necessary permissions for the `check-app-health` CronJob to perform actions like deleting pods, we configure a **Role** and a **RoleBinding**. These resources ensure the CronJob has restricted access to the required operations within the namespace.

### Definitions:
- **Role**: Defines the set of permissions (e.g., read, write, delete) for resources within a specific namespace.
- **RoleBinding**: Associates a Role with a user, group, or service account, granting them the defined permissions.
- Apply the configurations to create the Role and RoleBinding:

    ```bash
    kubectl apply -f role.yaml
    kubectl apply -f roleBinding.yaml
    ```

## 4. Monitoring Application Health with a Kubernetes CronJob

We use a Kubernetes CronJob to ensure that the application is accepting requests. If the application becomes unresponsive, the CronJob automatically deletes the application pods and retries after a delay. This setup helps maintain the application's availability without manual intervention.

### Steps:
1. **Define the CronJob**  
   Create a `check-app-health.yaml` file with the CronJob configuration. Ensure the CronJob performs the health check and handles unresponsive pods as required.

2. **Apply the Configuration**  
   Deploy the CronJob to your Kubernetes cluster using the following command:
   ```bash
   kubectl apply -f check-app-health.yaml

## 5. Network Security for Database Pods
To enhance security, we restrict the database pods (mysql) to accept ingress network traffic only from the application pods (orangeapp). This is achieved using a Kubernetes NetworkPolicy.

- Define the NetworkPolicy:
  - Create a mysql-network-policy.yaml file 
- Apply the Configuration:
  ```bash
  kubectl apply -f mysql-network-policy.yaml
  ```

## 6. Database Deployment & Exposing

Deploy the database using a Kubernetes Deployment. The Deployment manages the lifecycle of the database, ensuring the correct number of replicas are running and that it uses the Persistent Volume Claim (PVC) for storage. The database will be exposed via a ClusterIP service to allow access within the cluster.

### Steps:
1. Define a Deployment in your configuration, specifying the number of replicas and container details.
2. Apply the configuration to deploy the database application:

    ```bash
    kubectl apply -f Database.yaml
    ```

## 7. Application Deployment & Exposing

Deploy the application using a Kubernetes Deployment. To make the application accessible externally, create a Kubernetes Service of type NodePort. This service routes external traffic to the application's pods through a specific port (in this case, `port: 30036`) on each node in the cluster. Also, We are using secrets for SECRET_KEY in Djnago application.

### Steps:
1. Define a Service of type `NodePort` in your configuration.
2. Apply the configuration to create the Service:

    ```bash
    kubectl apply -f Secrets.yaml
    kubectl apply -f Application.yaml
    ```

## 8. Verify Deployment

After applying the configurations, you can check the status of your resources to ensure everything is set up correctly:

```bash
# Optional: Check other resources if needed
echo "Checking services..."
kubectl get svc -n macarious

echo "Checking deployments..."
kubectl get deploy -n macarious

echo "Checking pods..."
kubectl get pods -n macarious
```

## 9. Accessing the Application
- You will be aple to access the application using the `NodePort` defined in the Service (e.g., `http://<NodeIP>:30036`).

- By following these steps, you will successfully deploy your application on Minikube using Kubernetes. The namespace, persistent storage, database, and application will be properly configured and accessible.
