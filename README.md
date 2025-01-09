# bm-capi-gitops-demo


Local demo of argo cd gitops to create (and manage lifecycle of) worker clusters

```
# use kind to create "mgmt" cluster
# install capi on cluster

# install argo cd
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# fetch argo cd password
kubectl -n argocd get secret argocd-initial-admin-secret -o json | jq -r '.data.password' | base64 --decode

# login to argo ui 
kubectl port-forward svc/argocd-server -n argocd 8080:443
http://localhost:8080/

```