# Deployment on Minikube
This guide explains how to deploy an application on Minikube using Kubernetes `kubectl`. It covers the creation of a namespace, setup of persistent storage, initialization of data, deployment of the Database & application.

  ![K8s](/Figures/Kubernetes_logo.png)


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

## 3. Data Initialization with a Kubernetes Job

We use a Kubernetes Job to copy initial MYSQL data into the persistent storage. This job ensures that required data is available in the persistent volume before the application starts.

### Steps:
1. Define a Job in your Kubernetes configuration that copies the data.
2. Apply the configuration to run the job and initialize the data:

    ```bash
    kubectl apply -f Job.yaml
    ```

## 4. Database Deployment & Exposing

Deploy the database using a Kubernetes Deployment. The Deployment manages the lifecycle of the database, ensuring the correct number of replicas are running and that it uses the Persistent Volume Claim (PVC) for storage. The database will be exposed via a ClusterIP service to allow access within the cluster.

### Steps:
1. Define a Deployment in your configuration, specifying the number of replicas and container details.
2. Apply the configuration to deploy the database application:

    ```bash
    kubectl apply -f Database.yaml
    ```

## 5. Application Deployment & Exposing

Deploy the application using a Kubernetes Deployment. To make the application accessible externally, create a Kubernetes Service of type NodePort. This service routes external traffic to the application's pods through a specific port (in this case, `port: 30036`) on each node in the cluster.

### Steps:
1. Define a Service of type `NodePort` in your configuration.
2. Apply the configuration to create the Service:

    ```bash
    kubectl apply -f Application.yaml
    ```

## 6. Verify Deployment

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

## 7. Accessing the Application
- You will be aple to access the application using the `NodePort` defined in the Service (e.g., `http://<NodeIP>:30036`).

- By following these steps, you will successfully deploy your application on Minikube using Kubernetes. The namespace, persistent storage, database, and application will be properly configured and accessible.
