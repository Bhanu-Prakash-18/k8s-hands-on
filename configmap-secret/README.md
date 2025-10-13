# Kubernetes Hands-on: ConfigMaps & Secrets

This folder contains hands-on examples of **ConfigMaps** and **Secrets** in Kubernetes.  
It demonstrates how to manage application configuration and sensitive data securely.

## Folder Structure

configmap-secret/
├── app-config.yaml # ConfigMap definition
├── configmap-pod.yaml # Pod using ConfigMap
├── app-secret.yaml # Secret definition
├── secret-pod.yaml # Pod using Secret
└── README.md 


## 1. ConfigMaps
- Used to store **non-sensitive configuration data**.
- Can be mounted as **environment variables**, **files**, or **command-line arguments**.
- Example: `app-config.yaml` defines `APP_NAME` and `APP_ENV`.
- Pod `configmap-pod.yaml` consumes these values as environment variables.

## 2. Secrets
- Used to store **sensitive information** like passwords or API keys.
- Data is **base64 encoded** (not encrypted by default).
- Example: `app-secret.yaml` defines `DB_USER` and `DB_PASS`.
- Pod `secret-pod.yaml` consumes these values as environment variables.

## 3. Apply in Kubernetes
```bash
kubectl apply -f app-config.yaml
kubectl apply -f configmap-pod.yaml
kubectl apply -f app-secret.yaml
kubectl apply -f secret-pod.yaml

To Verify Pods use 

kubectl get pods

kubectl exec -it configmap-demo -- sh
echo $APP_NAME
echo $APP_ENV
exit

kubectl exec -it secret-demo -- sh
echo $DB_USER
echo $DB_PASS
exit

