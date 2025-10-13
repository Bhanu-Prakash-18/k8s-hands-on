# Kubernetes Hands-on: Scaling & Rolling Updates

This folder contains hands-on examples of **Scaling and Rolling Updates** in Kubernetes using Deployments.

## Folder Structure

scaling-rolling/
├── scaling-demo.yaml # Deployment with replicas
├── scaling-service.yaml # Service to expose pods
└── README.md # Notes & instructions


1. Scaling (Replicas)
 - **Purpose:** Run multiple copies of a pod to handle more load and improve availability.
 - **Defined in Deployment YAML:** `replicas: <number>`
 - **Example Commands:**
```bash
kubectl get deployment scaling-demo
kubectl scale deployment scaling-demo --replicas=5
kubectl get pods

2. Rolling Updates

Purpose: Update applications without downtime.
How: Update the container image in Deployment; old pods are replaced gradually.
Example Commands:
kubectl set image deployment/scaling-demo nginx=nginx:alpine
kubectl rollout status deployment/scaling-demo

3. Rollback

Purpose: Revert to the previous working version if an update fails.
Example Commands:
kubectl rollout undo deployment/scaling-demo
kubectl rollout history deployment/scaling-demo


