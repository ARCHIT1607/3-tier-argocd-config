# 3-Tier Full Stack Application with ReactJS, Spring Boot, and PostgreSQL

This repository demonstrates a full-stack web application with a ReactJS frontend, Spring Boot backend, and PostgreSQL database. The application is containerized using Docker, and Kubernetes manifests are provided for deploying the application on a local Minikube cluster using ArgoCD for GitOps.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for deployment and testing purposes.

## Prerequisites

Before you begin, ensure you have the following installed:
- **Docker** - [Link](https://docs.docker.com/engine/install/)
- **Minikube** - [Link](https://minikube.sigs.k8s.io/docs/start/)
- **Kubectl** - [Link](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)
- **ArgoCD** - [Link](https://argo-cd.readthedocs.io/en/stable/getting_started/)

### Installation

After you're done installing the tools.

- **Clone GitHub repository** <br>
    Find a location on your computer where you want to store the project. Now, run the following command to pull the project from GitHub and create a copy of it. And `cd` into the project.
    ```
    https://github.com/ARCHIT1607/3-tier-argocd-config.git
    ```
    
    
- **To deploy the project without using ArgoCD** <br>
    Use the following Kubectl commands.
    ```
    kubectl apply -f .\Dev\
    ```
    To test if the deployment is successful through UI
    visit the below Url to access UI and perform the tasks
    ```
    http://127.0.0.1:3000/
    ```


- **To deploy the project using ArgoCD** <br>
    Use port-forward to access the ArgoCD dashboard
    ```
    kubectl port-forward -n argocd svc/argocd-server 9000:443
    ```
    Access the dashboard by getting the password
    ```
    kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
    echo base64_encoded_text | base64 --decode
    ```

    You will find no application is deployed yet for achieving this use below command in terminal of project directory
    ```
    kubectl apply -f .\application.yml
    ```

    Once the status of application is Synced.

    To test if the deployment is successful through UI
    visit the below Url to access UI and perform the tasks
    ```
    http://127.0.0.1:3000/
    ```
    
- **To see syncing in action** <br>
    Update the k8 manifest files through git and ArgoCD will poll the changes every 3 times so once it observes the desired state
    is different from current state the ArgoCD server will sync the new changes with the old file and the updated manifest files
    will be deployed.
    
## Author

* **Archit Maniyath**  ([Archit1607](https://github.com/ARCHIT1607))