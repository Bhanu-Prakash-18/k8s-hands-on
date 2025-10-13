# Kubernetes Practice: Nginx Pod

## Objective
Deploy a simple Nginx Pod declaratively using YAML and practice basic kubectl commands.

## Steps Taken
1. Created a folder for Pod examples: `kubernetes-practice/pod-examples`
2. Created `nginx-pod.yaml` with:
   - `apiVersion: v1`
   - `kind: Pod`
   - metadata name: `my-nginx`
   - labels: `app: nginx`
   - container: nginx image, port 80
3. Applied the pod:
   ```bash
   kubectl apply -f nginx-pod.yaml
   kubectl get pods

Declarative approach uses YAML files, not imperative kubectl run.

kubectl get pods and kubectl describe pod <pod_name> help verify status and debug.
