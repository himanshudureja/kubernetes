# Imperitive way commands in Kubernetes 

#### Creating an nginx Pod:
kubectl run nginx --image nginx

#### Dry run for a pod:
kubectl run deomo --image=nginx --dry-run=client -oyaml

#### Check all the namespces:
kubectl get namepaces

#### Create a deployment
kubectl create deploy nginx --image=nginx

#### Create a namespace:
kubectl create ns dev

#### Describe a namespace 
kubectl describe ns dev

#### Delete the namespace 
kubectl delete ns dev

#### Switch the namespace
kubectl config set-context --current --namespace=dev

#### See labels of a pod 
kubectl get pods --show-labels 

#### Add label in a pod
kubectl label pod app=front-end

#### Search for pod with label type=frontend

[root@k8s-master ~]# kubectl get pods -l type=frontend  
NAME                     READY   STATUS    RESTARTS      AGE  
myapp-pod                1/1     Running   6 (30m ago)   255d  
nginx-6799fc88d8-5bjxz   1/1     Running   0             8m16s  

#### Describe a Pod
kubectl desribe pod

#### Check the logs of the Pod
kubectl logs -f <pod-name>

#### Delete a container 
kubectl delete pod <pod-name>

#### Forcefully delete a pod
kubectl delete pod <pod-name> --force

#### Go inside a container/Get shell access
kubectl exec -it nginx  bash

#### Create a pod using a yml file
kubectl apply -f pod.yml

#### Create a deplpymet
kubectl create deploy nginx --image=nginx

#### Check the deployment
kubectl get deployment 

#### Increase the number of replicas
kubectl scale deploy nginx --replicas=5 

#### Edit the deployment file on the fly
kubectl edit deploy nginx

#### Describe the Deployment
kubectl describe deploy nginx

#### Change the image of a deployment
kubectl set image deployment/nginx nginx=nginx:1.15.2 --record

#### Check the rollout history
kubectl rollout history deployment demo

#### Rollback the Deployment to older revision
kubectl rollout undo deployment nginx --to-revision 2

#### List of Network namespace
ip netns list

#### List all the namespace
lsns | grep nginx   (get the pid)  
lsns -p pid  











