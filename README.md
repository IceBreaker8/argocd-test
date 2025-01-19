## Accessing the cluster

1 - Install kubeconfig from your cloud provider's managed k8s cluster
2 - Replace the .kube/config file with the kubeconfig.yaml (without any file extensions)
3 - Install argoCD:
```
https://argo-cd.readthedocs.io/en/stable/getting_started/
```
4 - You apply the application.yaml file once:
```
kubectl apply -f .\application.yaml
```

## ArgoCD as context namespace (no need for -n namespace)
kubectl config set-context --current --namespace=argocd
