## Manual Scheduling
#### Assign the nodename to the pod definition file
Under the spec section add **nodeName: node01**

#### Lables and Selectors
kubectl get pods --selector="env=prod"  --selector="bu=finance"

#### Taints and Tolerations 
Taints are applied at nodes ,  Tolerations are applied at Pod
kubectl taint nodes node-name key=value:taint-effect

Taint effects : NoSchedule, PreferNoSchedule, NoExecute

```tolerations:
  -key: "app"
   operator: "Equal"
   value: "blue"
   effect: "NoSchedule"
```   

#### Check the Taints
kubectl describe node kubemaster | grep Taint

#### Remove the taint from control plane node
kubectl taint node controlplane node-role.kubernetes.io/control-plane:NoSchedule-

#### Node Selector
under the spec section, add below:

nodeSelector:
  size: large 

#### Label the Node
kubectl label nodes node1 size=large

#### Display or get the labels of the node
kubectl get node node01 --show-lables

#### Node Affinity 

```
affinity:
 nodeaffinity:
  requiredDuringSchedulingIgnoredDuringExecution:
   nodeSelectorTerms:
    - matchExpressions:
      -key : size
       operator : In
       values: 
       - Large
       - Medium
```       
```       
affinity:
  nodeAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
      nodeSelectorTerms:
        - matchExpressions:
          - key: node-role.kubernetes.io/control-plane
            operator: Exists      
```            
       
       



  
















