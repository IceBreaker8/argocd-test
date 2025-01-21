

## Accessing the cluster

1 - Install kubeconfig from your cloud provider's managed k8s cluster
2 - Powershell: [System.Environment]::SetEnvironmentVariable("KUBECONFIG", "C:\path\to\your\kubeconfig.yaml", "User")

## Prerequisite

# Install ArgoCD: 
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
Get ArgoCD password and decode the base64 (change it later):
```
kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
```
# Install ArgoCD: 

## Install Helm on local (to be able to use the helm CLI)

winget install Helm.Helm

## ArgoCD as context namespace (no need for -n namespace)

kubectl config set-context --current --namespace=argocd

## Access argoCD locally through port forward

kubectl port-forward svc/argocd-server -n argocd 8080:443

## cleanup application sets

kubectl delete applicationsets --all -n argocd

## cleanup namespaces

kubectl get namespaces
kubectl delete namespace myapp

## Port forward (get services first by namespace to check their type and port )

kubectl port-forward svc/kube-prometheus-stack-grafana 8001:80 -n kube-prometheus-stack

## Check all PVCs in all namespaces

kubectl get pvc -A

##TIPS:

For postgres deplyoments, make a PVC and a statefulset yaml instead of deployment
https://chatgpt.com/share/678ebf50-9518-8001-8182-d0d39c7f12ee

HttpRoute (instead of ingress), gateway and cert
https://chatgpt.com/share/678ebf50-9518-8001-8182-d0d39c7f12ee