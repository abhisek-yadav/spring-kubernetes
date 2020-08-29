# spring-kubernetes

### Spring boot application using Redis as cache deployed on Kubernetes Cluster.

Details of the docker image used as part of this exercise can be found in the given below project:

https://github.com/abhisek-yadav/spring-dockercompose

This image is published to the Docker Hub as well. You can pull the image by using the given below command:

`docker pull abhisekyadav/spring-dockercompose`

<br/>
<br/>

## Commands to start Kubernetes cluster:
<br/>

##### 1. To start the cluster:

  `minikube start`

  The above command will start the Kubernetes cluster. 

- To get more details of running Kubernetes cluster:

  `minikube status`
  `minikube ip`

- To point our shell/terminal to minikube's docker-daemon:

  `eval $(minikube -p minikube docker-env)`

  Once we are connected to docker-daemon inside Kubernetes, we can execute all the commands supported by docker-cli. 


- To open the terminal (this is required when we use Docker driver on darwin):

  `minikube service boot-service --url`

  The above command will start a tunnel for the above-mentioned service.

<br/>

##### 2. To get the details from running Kubernetes cluster:

- To pass the configuration to the running cluster (Declarative Approach):

  `kubectl apply -f boot-pod.yaml` 
  `kubectl apply -f boot-service.yaml`

- To get the running objects(Pod, Service, Deployment etc.):

  `kubectl get pods`
  `kubectl get services`
  `kubectl get deployments`

- To describe a running pod:

  `kubectl describe pod  boot-pod`

- To get the logs of a running container:

  `kubectl logs boot-pod springboot-app`
