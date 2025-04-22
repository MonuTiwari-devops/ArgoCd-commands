# ArgoCd-commands
# ArgoCD Demo Project

## Prerequisites
- Kubernetes cluster (Minikube, Kind, or EKS/GKE)
- ArgoCD installed
- GitHub repo with Kubernetes manifests (you're looking at it)

## ArgoCD Installation
\`\`\`bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get pods -n argocd --watch
kubectl port-forward svc/argocd-server -n argocd 8080:443
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
\`\`\`

## Open ArgoCD UI
Login: http://localhost:8080  
Username: \`admin\`  
Password: (output from command above)

## Demo App: NGINX

This repo includes:
- \`nginx-deployment.yaml\`: A basic NGINX deployment manifest

## Usage in ArgoCD UI
- Application Name: \`nginx-demo\`
- Repo URL: this repo
- Path: \`/\`
- Cluster: \`https://kubernetes.default.svc\`
- Namespace: \`default\`
- Sync Policy: Manual
EOF
