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

![image](https://user-images.githubusercontent.com/88186581/135874162-e96b66a8-c8a6-462f-a8df-abb3ac8f0a96.png)

`kubectl get service`
```bash
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   73m
```

















