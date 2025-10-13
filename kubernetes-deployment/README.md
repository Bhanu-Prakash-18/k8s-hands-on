# Kubernetes Deployment & Service Hands-On

This project contains YAML files for practicing Kubernetes **Deployment** and **Service**.  
It also serves as a **quick reference guide** for next time.

---

## 1.  Project Structure

kubernetes-deployment/
├── nodejs-deployment.yaml
└── nodejs-service.yaml

Deployment manages pods; it ensures desired state, scaling, and updates.

replicas: number of pods to run (here 3).

selector.matchLabels: must match template.metadata.labels. This tells Deployment which pods it manages.

template.metadata.labels: labels applied to pods. These must match Deployment selector.

Always ensure labels match correctly, otherwise Deployment won’t manage pods properly.

Service type NodePort: exposes service on a port accessible from outside the cluster.

selector: must match Deployment pod labels (app: nodejs-app).

Access app: http://<EC2-Public-IP>:<NodePort>.

(or)   http://<Node-IP>:<NodePort>

kubectl apply -f nodejs-deployment.yaml
kubectl apply -f nodejs-service.yaml

kubectl get deployments
kubectl get pods
kubectl get svc

kubectl scale deployment nodejs-deployment --replicas=5
kubectl get pods



