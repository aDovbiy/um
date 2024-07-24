# GitHub Repo for Helm Charts and ArgoCD
## Overview
Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.
This repo include a CI/CD pipeline for validating and publishing 
Helm charts, with support for pushing these charts as OCI images to the 
GitHub Container Registry (GHCR) include ArgoCD for manage itself and deploy specific Kubernetes components.

For this sample used Community Charts as Umbrella Charts: Incorporate community Helm charts as umbrella charts for managing complex deployments.
Implement Build a CI/CD Pipeline using GitHub Actions that validates and publishes Helm charts to the repo and as OCI images to GHCR.

Repository organization:
File https://github.com/aDovbiy/um/blob/main/.github/workflows/workflow.yaml contains the automation script for pushing to the master branch.
Repository has two subsystems:
Fully automatic Argo management (argocd-app-chart)
Automatic deployment of diagrams to GitHub Container Registry (GHCR) as OCI images (Our APPs) umbrella-app-chart
All secrets and authorization parameters are hidden in the secret manager and are accessible only to the administrator

### All workflows https://github.com/aDovbiy/um/actions

#### ArgoCD  Connection
```ShellSession
# Use for auth in ArgoCD
kubectl get secret argocd-initial-admin-secret -o jsonpath={.data.password} --namespace argocd | base64 -d

# Use for connect to ArgoCD over kubectl port-forward
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
##### Files for manage ArgoCD

https://github.com/aDovbiy/um/blob/main/argocd-app-chart/custom/applications.yaml

##### Files for manage Umbrella Chart

https://github.com/aDovbiy/um/blob/main/umbrella-app-chart/Chart.yaml

https://github.com/aDovbiy/um/blob/main/umbrella-app-chart/values.yaml


![image](https://github.com/user-attachments/assets/3ea362ff-fbf3-48a2-af87-495daa370a24)

![image](https://github.com/user-attachments/assets/d1c5f402-47a8-4e60-927b-595078d878e3)

![image](https://github.com/user-attachments/assets/c640c137-9bcc-46a5-8c88-8aca0c2bb749)

!





