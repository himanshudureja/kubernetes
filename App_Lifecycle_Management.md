### Rolling Update and Rollbacks

#### Check the status of the Rollout of the deployment
kubectl rollout status deployment/myapp-deployment

#### Check the history of the Rollout
kubectl rollout history deployment/myapp

#### Rollback or Undo the Deployment
kubectl rollout undo deployment/myapp

### Commands ad Arguments

```
spec:
  containers:
  - name: nginx
    image: nginx
    command: ["sleep"]
    args: ["100"]
```

