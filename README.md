# Kubernetes

![image](https://user-images.githubusercontent.com/88186581/135876352-bb3b044a-cba2-456d-b76f-a02b274f41af.png)

## What is Kubernetes?

- orchastration tool
- most organisations adopt kubernetes
- autoscaling and load balancing

### How does it work with Docker?

- manage containers - docker
- developed and run by Google for over 15 years

![image](https://user-images.githubusercontent.com/88186581/135854674-21d46186-a46b-45c4-9585-3a2df4f58eb2.png)
![image](https://user-images.githubusercontent.com/88186581/135854776-2257d805-20e7-4aa3-93b2-6f9294321141.png)

- running a container - individual
- k8 allows for multiple replicas - facillitates the user if one container goes down
- makes app highly available and sclable

### Automation

![image](https://user-images.githubusercontent.com/88186581/135855301-3ca1cd63-bbc6-42fb-ba01-033e14735678.png)

### What are its benefits?

- self-healing
- automated rollouts and rollbacks if system fails (v1 --> v2 --> v1)
- automatic bin packing

## Installation

### Creating the cluster:
- Run and open Docker
- Go to Settings
- Enable Kubernetes --> apply and restart
- Restart computer and Docker
- Both are running, it should look like this:

![image](https://user-images.githubusercontent.com/88186581/135873961-49dff8b4-ff11-4d1c-895b-d94080ce03a3.png)

#### In the terminal: 

`kubectl` to see all commands

![image](https://user-images.githubusercontent.com/88186581/135875521-7bf6590e-4997-418e-ad68-3b4afb640af3.png)

`kubectl version`

![image](https://user-images.githubusercontent.com/88186581/135877957-eb27ee74-2b77-443e-8b17-0712c8c3eaed.png)

`kubectl get service`
```bash
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   73m
```

## Setting Up

- create `nginx-deploy.yml` file in new folder

```yaml
# K8 works w API versions to declare the resources
# We have to declare the apiVersion ans the kind of service/component

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment # Naming the deployment

spec:
  selector:
    matchLabels:
      app: nginx # Look for this label to mtch w K8 service

  # Let's creatw a replica set of this with 2 instances/pods
  replicas: 2

  # Template to use its label for K8 service to launch in the browser
  template:
    metadata:
      labels:
        app: nginx # This label connects to the service

    # Let's define the container spec
    spec:
      containers:
        - name: nginx
          image: akunduj/sre_node_app:v1
          ports:
          - containerPort: 80
          
```
- create the file:
`kubectl create -f "YAML_file_name.extention"`

![image](https://user-images.githubusercontent.com/88186581/135880729-392dee03-a51e-4981-80a3-d2738a65b9d0.png)

`kubectl get deploy`

![image](https://user-images.githubusercontent.com/88186581/135880775-61e64ca3-b678-48d3-bd81-e5c6b8f6be21.png)

`kubectl get pods`

![image](https://user-images.githubusercontent.com/88186581/135880821-c5968c43-7502-486e-99b6-c58604848a49.png)

`kubectl describe pod "POD_NAME"`

![image](https://user-images.githubusercontent.com/88186581/135881406-ab6a95eb-019b-4198-a665-6251dce059e1.png)

`kubectl describe deploy "DEPLOYMENT_NAME"`

![image](https://user-images.githubusercontent.com/88186581/135881953-22a54c38-4a5e-45c4-9942-f78d68333dcd.png)

`kubectl edit deploy "DEPLOYMENT_NAME"` --> change configurations of deployment

opens notepad
change no of replicas 2 --> 3
save file and exit

### rewatch monday afternoon 


Create a `nginx-service.yml` file

```yaml
---

apiVersion: v1
kind: Service
# Metadata for name
metadata:

  name: nginx-deployment
  namespace: default

spec:
  ports:
  - nodePort: 30442
    port: 80
    protocol: TCP
    targetPort: 80

  
# Lets define the selector and label
  selector:
    app: nginx # This label connects this service to deployment

  # Creatikng LoadBalancer type of deployment
  type: LoadBalancer
```

`kubectl get service`
```bash
NAME               TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
kubernetes         ClusterIP      10.96.0.1        <none>        443/TCP        127m
nginx-deployment   LoadBalancer   10.110.221.129   localhost     80:30442/TCP   10s
```

`kubectl delete pod "POD NAME"`
- if set up correctly with the replicas, then deleting a pod will not affect the `LocalHost` webpage

`kubectl get all` - list all running

`kubectl delete svc "SERVICE NAME"` - delete a service

connect pod to deployment using the same label --> label_match == True --> connected, can see in browser

#### rewatch tues morning

## Define

### Cluster
### Pods
### Services
### Deployment
### API
### Objects
### HPA

## Node App and MongoDB

![image](https://user-images.githubusercontent.com/88186581/136015561-6299266c-bead-4e0f-b63f-a8bec2453178.png)
