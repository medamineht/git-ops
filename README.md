# git-ops
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

Using the username admin and the password from above, login to Argo CD's IP or hostname:
argocd login <ARGOCD_SERVER>

Change the password using the command:
argocd account update-password
