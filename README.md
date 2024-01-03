# 3-Tier Full Stack Application with ReactJS, Spring Boot, and PostgreSQL

This repository demonstrates a full-stack web application with a ReactJS frontend, Spring Boot backend, and PostgreSQL database. The application is containerized using Docker, and Kubernetes manifests are provided for deploying the application on a local Minikube cluster using ArgoCD for GitOps.

Docker Images for frontend and backend were created using https://github.com/RameshMF/ReactJS-Spring-Boot-CRUD-Full-Stack-App/tree/master repo source code so shout out to him.

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
    ![ArgoCD Dashboard](images/argocd-dashboard.png)

    To test if the deployment is successful through UI
    visit the below Url to access UI and perform the tasks
    ```
    http://127.0.0.1:3000/
    ```

     ![UI](images/application.png)
    
- **To see syncing in action** <br>
    Update the k8 manifest files through git and ArgoCD will poll the changes every 3 times so once it observes the desired state
    is different from current state the ArgoCD server will sync the new changes with the old file and the updated manifest files
    will be deployed.


## Project Motivation

## Background

In the rapidly evolving landscape of modern web development, we identified a growing need for a comprehensive full-stack application that seamlessly integrates ReactJS, Spring Boot, and PostgreSQL. Through our experience in the field, we observed that many developers faced challenges when trying to set up, deploy, and manage such applications, leading to inefficiencies in the development process.

## Problem Statement

Developers often encounter complexities in configuring and deploying a 3-tier architecture application with ReactJS, Spring Boot, and PostgreSQL. The lack of a standardized and straightforward solution results in wasted time, potential errors in the deployment process, and a steep learning curve for those new to the technology stack.

## Objectives

- Simplify the development and deployment workflow for a 3-tier application.
- Provide a well-documented and easy-to-follow template for integrating ReactJS, Spring Boot, and PostgreSQL.
- Foster best practices in containerization using Docker and orchestration with Kubernetes and ArgoCD.

## Why This Stack?

ReactJS offers a dynamic and efficient frontend experience, while Spring Boot provides a robust and scalable backend. PostgreSQL serves as a reliable and powerful relational database, creating a well-rounded technology stack suitable for a wide range of applications. Docker ensures consistency across different environments, and Kubernetes, combined with ArgoCD, simplifies the deployment and management of containerized applications.

## Learning Goals

Our primary learning goals include mastering the integration of these technologies, understanding best practices for microservices architecture, and gaining hands-on experience with Kubernetes and GitOps principles through ArgoCD.

## Expected Outcomes

- Streamlined development process for 3-tier applications.
- Improved collaboration and knowledge-sharing among developers working with ReactJS, Spring Boot, and PostgreSQL.
- Enhanced understanding of Docker, Kubernetes, and ArgoCD.

## Target Audience

This project caters to developers, DevOps engineers, and technology enthusiasts who are interested in building and deploying scalable, modern web applications. By providing a comprehensive example, we aim to assist both beginners and experienced developers in mastering the intricacies of this technology stack.
    
## Author

* **Archit Maniyath**  ([Archit1607](https://github.com/ARCHIT1607))