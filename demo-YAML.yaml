Lanch EC2-instance t2.micro 

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html


#### Pre-requisites: 
  - an EC2 Instance 
  - Install AWSCLI latest verison 

1. Setup kubectl   
   a. Download kubectl version 1.21  
   b. Grant execution permissions to kubectl executable   
   c. Move kubectl onto /usr/local/bin   
   d. Test that your kubectl installation was successful    

   ```sh 
   curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/kubectl
   chmod +x ./kubectl
   mv ./kubectl /usr/local/bin 
   kubectl version --short --client
   ```
2. Setup eksctl   
   a. Download and extract the latest release   
   b. Move the extracted binary to /usr/local/bin   
   c. Test that your eksclt installation was successful   

   ```sh
   curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   sudo mv /tmp/eksctl /usr/local/bin
   eksctl version
   ```
  
3. Create an IAM Role and attache it to EC2 instance    
    https://eksctl.io/usage/minimum-iam-policies/
   
   
   ##create a admin role and provide to the ec2-instance
   
  

   eksctl create cluster --name hippo-cluster \
      --region ap-south-1 \
   --node-type t2.small 
   
	
	
	kubectl get all
	kubectl create deployment demo-nginx --image=nginx --port=80 --replicas=2
	kubectl get deployment / kubectl get deploy
	kubectl get replicaset
	kubectl get pod  //kubectl get pods
	kubectl get all
	kubectl expose deployment demo-nginx --port=80 --type=LoadBalancer
	kubectl get all
	kubectl delete deployment demo-nginx
	kubectl delete service/demo-nginx


## pod.yml

apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: demo-app

spec:
  containers:
  - name: nginx-container
    image: nginx
    ports:
    - name: nginx 
      containerPort: 80
	  
	  kubectl apply -f pod.yml  // once pod created then need to create service
	  
	  
## service.yml

apiVersion: v1
kind: Service
metadata:
  name: demo-service
  
spec:
  ports:
  - name: nginx-port
    port: 80
    targetPort: 80
  type: LoadBalancer	
  
--------

## pod1.yml  // label set into servic yam in selector

apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: demo-app

spec:
  containers:
  - name: nginx-container
    image: nginx
    ports:
    - name: nginx 
      containerPort: 80  
  
## service1.yml

apiVersion: v1
kind: Service
metadata:
  name: demo-service
  
spec:
  ports:
  - name: nginx-port
    port: 80
    targetPort: 80
	
  selector:
    app: demo-app
	
  type: LoadBalancer  
  
  
    kubectl apply -f pod.yml
	kubectl apply -f service.yml
	
	kubectl describe service/demo-service
	
	 kubectl get pod -o wide
	 
	 kubectl get all
	 
	 kubectl delete pod nginx-pod
	 
	 kubectl delete service/demo-service
	 
	 kubectl get pod
	 
	 kubectl get all

###pod2.yml

apiVersion: apps/v1 
kind: Deployment
metadata:
  name: hippo
  labels: 
     app: sampleapp

spec:
  replicas: 2 
  selector:
    matchLabels:
      app: sampleapp

  template:
    metadata:
      labels:
        app: sampleapp
    spec:
      containers:
      - name: sampleapp
        image: dockerpandian/project
        imagePullPolicy: Always
        ports:
        - containerPort: 8080
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1
	  

## service2.yml
	  
apiVersion: v1
kind: Service
metadata:
  name: hippo-service
  labels:
    app: sampleapp 
spec:
  selector:
    app: sampleapp 

  ports:
    - port: 8080
      targetPort: 8080

  type: LoadBalancer	  
  
  kubectl apply -f pod2.yml

  kubectl apply -f service2.yml
	
	
	kubectl get pod
    kubectl get all
    kubectl get pod -o wide
   kubectl get all
   kubectl get po
   kubectl delete pod hippo-588c8968f4-qqdz8
    kubectl get po
	kubectl get all
	kubectl delete deployment.apps/hippo
	kubectl get all
	kubectl delete service/hippo-service
	kubectl get nodes
	eksctl delete cluster hippo-cluster --region ap-south-1
	
