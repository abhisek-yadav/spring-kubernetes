# spring-kubernetes

### Spring boot application using Redis as cache deployed on Kubernetes Cluster.

Details of the docker image used as part of this exercise can be found in the given below project:

https://github.com/abhisek-yadav/spring-dockercompose

<br/>

This image is published to the Docker Hub as well. You can pull the image by using the given below command:

         docker pull abhisekyadav/spring-dockercompose

<br/>

Link to Docker Hub: https://hub.docker.com/r/abhisekyadav/spring-dockercompose

<br/>
<br/>

## Commands for minikube:
<br/>

##### 1. To start the cluster:

         minikube start

###### The above command will start the Kubernetes cluster. 

##### 2. To stop the cluster:

         minikube stop


##### 3. To get more details of running Kubernetes cluster:

         minikube status
         minikube ip


##### 4. To point our shell/terminal to minikube's docker-daemon:

         eval $(minikube -p minikube docker-env)

###### Once we are connected to docker-daemon inside Kubernetes, we can execute all the commands supported by docker-cli. 


##### 5. To open the terminal (this is required when we use Docker driver on darwin):

         minikube service boot-service --url

###### The above command will start a tunnel for the above-mentioned service.

<br/>
<br/>

## Commands for kubectl:
<br/>

##### 1. To create/update an object that is described in a configuration file (Declarative Approach):

         kubectl apply -f boot-pod.yaml
         kubectl apply -f boot-service.yaml
       
         
##### 2. To delete an object that is described in a configuration file:
         
         kubectl delete -f boot-pod.yaml
         kubectl delete -f boot-service.yaml
         
        
##### 3. To get the running objects(Pod, Service, Deployment etc.):

         kubectl get pods
         kubectl get services
         kubectl get deployments


##### 4. To describe a running pod:

         kubectl describe pod boot-pod


##### 5. To get the logs of a running container:

         kubectl logs boot-pod springboot-app
         
         
##### 6. To create/update pods using Deployment object:

         kubectl apply -f boot-deployment.yaml
         
###### Deployment objects are like a template for pods.


##### 7. To see the ReplicaSet (rs) created by the Deployment:

         kubectl get rs
         
         
##### 8. To see the labels automatically generated for each Pod:

         kubectl get pods --show-labels         
