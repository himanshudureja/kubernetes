## Logging and Monitoring 

In case metric server is installed
#### View the metrics of nodes
kubectl top node

#### View the metrics of the pod
kubectl top pod

#### View the logs of a Pod
kubectl logs -f pod-name

#### View the logs of a container in case of multiple container in a pod
kubectl logs -f pod-name container-name

