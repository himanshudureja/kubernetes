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

### Env variables in Kubernetes

#### Direct specify the environment variable in pod definition file
```
spec:
  containers:
  - name: simple-webapp-color
    image: webapp
    ports:
      - containerPort: 8080
    env:
      - name: APP_COLOR
        value: pink
```        

#### Specify the Config map

```
env:
 - name: APP_COLOR
   valueFrom:
      configMapKeyRef:
          name: app-config
          key: APP_COLOR
```

#### Specify the Secret

```
env:
 - name: APP_COLOR
   valueFrom:
      secretKeyRef:
```

#### Create config Map (Imperative way)

kubectl create configmap \
      app-config --from-literal=ENV=PROD \
                 --from-literal=APP_NAME=Frontend \
                 --from-literal=PORT=8080

#### Create config map (Imperative way) through a file

kubectl create configmap \
      app-config --from-file=us_int_prod_oss_config.properties
      
#### Create config map (Declarative way)

config-map.yaml
```
apiVersion: v1
kind: ConfigMap 
metadata:
  name: app-config
data:
  ENV: PROD
  APP_NAME: frontend
  PORT: 8080
```  

kubectl create -f config-map.yaml

#### View Config Maps
kubectl get configmaps

#### Describe Config Map
kubectl describe configmaps

#### Inject the config map inside the pod

- envFrom:
  - configMapRef:
        name: app-config

#### Create Secrets Imperative way

kubectl create secret generic mongo-secret \
   --from-literal=host=mongodb1.example.com \
   --from-literal=port=27017 \
   --from-literal=password=fjhfbfhf
   
#### Create Secrets Imperative way through a file

kubectl create secret generic mongo-secret --from-file=mongo-connection.properties 

#### Declarative way of creating secret

secret-db.yaml

apiVersion: v1
kind: Secret
metadata: 
  name: secret-db
data:
   DB_HOST:  445365ewdbsx2
   DB_USER: 47r6478r
   DB_PASSWORD: 847r847
   
#### To base64 encode a password

echo -n "password" | base64

#### To decode a base 64 encoded secret value

echo -n "ddg64748==" | base64 --decode

#### To view the secret
kubectl get secret

#### To describe the secret
kubectl describe secret name

#### To view the values of the secret
kubectl get secret db -o yaml




   
   

        









      
