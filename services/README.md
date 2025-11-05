Kubernetes Service — Concept & Hands-on
🔹 What is a Service?

A Service in Kubernetes provides a stable network endpoint to access a group of Pods.
Since Pods are ephemeral and their IPs change when restarted or recreated, a Service ensures consistent connectivity between applications.

🔹 Why do we use a Service?

Kubernetes Service solves two key problems:

Pod IPs are temporary

Every time a Pod is recreated, it gets a new IP.

Services give a stable virtual IP (ClusterIP) to access Pods consistently.

Load Balancing

When multiple Pod replicas exist, the Service automatically distributes traffic between them.

🔹 How does it work?

Services use labels and selectors to find the right Pods.

Example:

# Pod or Deployment labels
metadata:
  labels:
    app: nginx

# Service selector
selector:
  app: nginx


The Service automatically routes traffic to all Pods matching that label.

🔹 Service Types
Type	Description	Access
ClusterIP	Default type, internal access only	Inside cluster
NodePort	Exposes app via Node IP + static port	From browser / external
LoadBalancer	Used in cloud for public access	External IP from cloud
🔹 Commands used
# Create the Service
kubectl apply -f nginx-service.yaml

# List services
kubectl get svc

# Get Node IP (for Minikube)
minikube ip

# Access from browser
http://<minikube-ip>:<nodePort>

🧠 Example

If minikube ip = 192.168.49.2
and your Service NodePort = 30080,
then access:

http://192.168.49.2:30080


✅ You’ll see the Nginx welcome page.
