# Kubernetes Practice: Nginx Service

## Objective
Expose an existing Nginx Pod using a declarative Service YAML.

## Steps Taken
1. Created `nginx-service.yaml`:
   - `apiVersion: v1`
   - `kind: Service`
   - metadata: `name: my-nginx-service`
   - selector: `app: nginx`
   - ports: 80 → targetPort 80
   - type: NodePort
     
2. Applied the service:
   ```bash
   kubectl apply -f nginx-service.yaml
   kubectl get svc
   
## Accessing Service from Outside the Cluster
   - To access a Service externally, we use **NodeIP:NodePort** format.  
   - The **Node IP** can be found using:
    ```bash
     kubectl get nodes -o wide
The NodePort is assigned automatically by Kubernetes (or can be specified in YAML).
Instead of remembering NodeIP and NodePort, we can also use port-forwarding:
     kubectl port-forward svc/<service-name> <local-port>:<service-port>

3. Verified NodePort and accessed via port-forward:
   kubectl port-forward svc/my-nginx-service 8080:80
   curl http://localhost:8080

selector must match the Pod label (app: nginx).
NodePort is used to expose pods externally (useful for testing).
