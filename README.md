## Accessing the cluster

1 - Install kubeconfig from your cloud provider's managed k8s cluster
2 - Powershell: [System.Environment]::SetEnvironmentVariable("KUBECONFIG", "C:\path\to\your\kubeconfig.yaml", "User")
3 - Install argoCD using the kubectl CLI

```
https://argo-cd.readthedocs.io/en/stable/getting_started/
```

4 - You apply the application.yaml file once:

```
kubectl apply -f .\application.yaml
```

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
