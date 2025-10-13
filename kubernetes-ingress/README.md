# Kubernetes Ingress Hands-On

This project demonstrates **Kubernetes Ingress** for routing external traffic to multiple services in a cluster.

---

## 1️⃣ Project Structure

kubernetes-ingress/
├── nodejs-deployment.yaml
├── nodejs-service.yaml
├── nginx-deployment.yaml
├── nginx-service.yaml
└── ingress.yaml

**Ingress**: Manages external HTTP/HTTPS access to services.
- **Ingress Controller**: Actual implementation (e.g., NGINX) that routes traffic.
- **NodePort vs Ingress**:
  - NodePort: exposes each service externally on its own port.
  - LoadBalancer: exposes service with a cloud LB, one LB per service.
  - Ingress: allows multiple services to share **a single external IP / LB** and route traffic based on **host/path**, reducing cost and simplifying management.


http://myapp.local/nodejs
 -> Node.js Service
http://myapp.local/nginx
 -> Nginx Service

- Ingress annotations like `nginx.ingress.kubernetes.io/rewrite-target: /` are often needed to properly route traffic.


Without Ingress (using NodePort or Service of type LoadBalancer) : 

For each application, if you want external access, you need
NodePort → exposes the app on a port (30000–32767).
LoadBalancer → cloud provider creates a separate LB per Service.
Problem: If you have 5 apps, you get 5 separate load balancers, which is expensive and harder to manage.

With Ingress : 

Ingress acts as a single entry point for multiple services.
You only need one external Load Balancer, and Ingress routes traffic to the right Service based on:
Host (example: app1.example.com, app2.example.com)
Path (example: /app1, /app2)
This is much cost-efficient and easier to manage.
