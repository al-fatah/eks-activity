# 📘 Kubernetes Part 1 -- Hands-On Activity

This repository contains the Kubernetes manifests and evidence for the
**EKS Deployment Activity** performed on the shared AWS EKS cluster.

The activity includes: - Creating a namespace\
- Deploying an Nginx application\
- Exposing it via a LoadBalancer Service\
- Creating and attaching a ServiceAccount\
- Verifying all resources within the namespace

------------------------------------------------------------------------

## 🚀 1. Namespace Creation

Namespace created for this activity:

    kubectl create namespace alfatah-eks-activity

Verification:

    kubectl get namespaces

------------------------------------------------------------------------

## 📦 2. Deployment

File: `nginx-deployment.yaml`

Applies an Nginx Deployment with 2 replicas.

    kubectl apply -f nginx-deployment.yaml
    kubectl get deployments -n alfatah-eks-activity
    kubectl get pods -n alfatah-eks-activity

------------------------------------------------------------------------

## 🌐 3. Service

File: `nginx-service.yaml`

Exposes the deployment using a LoadBalancer service.

    kubectl apply -f nginx-service.yaml
    kubectl get svc -n alfatah-eks-activity

------------------------------------------------------------------------

## 🔐 4. Service Account

File: `service-account.yaml`

Creates a ServiceAccount for the Deployment.

    kubectl apply -f service-account.yaml
    kubectl get serviceaccount -n alfatah-eks-activity

Updating Deployment to use ServiceAccount:

    kubectl apply -f nginx-deployment.yaml

Verification:

    kubectl get deployment -o yaml -n alfatah-eks-activity | grep serviceAccount

------------------------------------------------------------------------

## ✅ Apply All Manifests

Optional convenience command:

    kubectl apply -f .

------------------------------------------------------------------------

## ✨ Conclusion

This activity demonstrates: - Understanding of Kubernetes resources\
- Ability to deploy workloads to EKS\
- Usage of namespaces for resource isolation\
- Service exposure using AWS LoadBalancer\
- Applying ServiceAccounts to deployments
