# ArgoCD Bootstrap GitOps-Operator (Public Repo)

This is an Testing Repository for ArgoCD as an GitOps-Operator to automatically deploy and manage Applications.

The ArgoCD autopilot makes it easy to add and manage applications with the autopilot CLI. The CLI autmatically pushes changes to the git-ops repo.

[argoproj-labs/argocd-autopilot](https://github.com/argoproj-labs/argocd-autopilot)

- Repo pattern: Monorepo
- Operator pattern: Instance per Cluster / Hub and Spoke
- Operator: ArgoCD
- Boostrapping: argocd-autopilot
- Linking: kustomization.yaml, ArgoCD Application, ApplicationSet
- Features:
    - Operate ArgoCD with GitOps

installation guide for the argocd-autopilot CLI: https://argocd-autopilot.readthedocs.io/en/stable/Installation-Guide/

## Recovery Repository in case of a new Cluster Instance

**MAC/UNIX**
```shell
export GIT_REPO=https://github.com/lambrech-hsrt/argocd-bootstrap
export GIT_TOKEN=PAT

argocd-autopilot repo bootstrap --recover
```

**Windows (Powershell)**
```shell
$env:GIT_REPO = "https://github.com/lambrech-hsrt/argocd-bootstrap"
$env:GIT_TOKEN = "PAT"

argocd-autopilot repo bootstrap --recover
```

After that you can start the ArgoCD UI and login with the default credentials at http://localhost:8080
```shell
kubectl port-forward -n argocd svc/argocd-server 8080:80
```

default password:
```shell
argocd admin initial-password -n argocd

```

## Deploy a new Application
```
argocd-autopilot app create <new_app_name> --app github.com/some_org/some_repo/manifests --project project_name
```
