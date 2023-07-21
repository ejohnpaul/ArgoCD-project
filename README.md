# Requirements:

# Installed kubectl command-line tool.
# Have a kubeconfig file (default location is ~/.kube/config).
# CoreDNS. Can be enabled for microk8s by microk8s enable dns && microk8s stop && microk8s start

# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd


# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -n argocd -o yaml

echo jsonpath="{.datapassword}" | base64 --decode

# You can change and delete init password
