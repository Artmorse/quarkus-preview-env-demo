# preview environment with argocd

## Prerequisites

- kind
- kubectl
- docker
- kubectx/kubens

## Argo CD set up

https://github.com/argoproj/argo-cd/releases/tag/v2.10.3

```bash
kind create cluster
kubectx kind-kind

kubectl create namespace argocd
kubens argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.10.3/manifests/install.yaml
```

The default ArgoCD admin username is `admin` and you can find the password using:
```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

You can use the kubernetes port-forward feature to access ArgoCD:
```bash
kubectl -n argocd port-forward service/argocd-server 8080:80
```

## Configure the preview environment for our demo application

Our demo application have Helm manifests defined in [preview/templates](/preview/templates) directory.

The github repository is public, so we don't need to manage any secrets.

We can configure the ArgoCD ApplicationSet to create a preview environment for each branch.

```bash
kubectl apply -n argocd -f argocd/applicationset.yaml
```
