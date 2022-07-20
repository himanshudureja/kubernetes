# Imperitive way commands in Kubernetes 

### Creating an nginx Pod:
kubectl run nginx --image nginx

### Dry run for a pod:
kubectl run deomo --image=nginx --dry-run=client -oyaml

### Check all the namespces:
kubectl get namepaces

### Create a namespace:
kubectl create ns dev

### Describe a namespace 
kubectl describe ns dev

### Delete the namespace 
kubectl delete ns dev

### Switch the namespace
kubectl config set-context --current --namespace=dev




