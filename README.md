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
         
         $ kubectl apply -f boot-pod.yaml
         pod/boot-pod created
         
         $ kubectl apply -f boot-service.yaml
         service/boot-service created
         
       
         
##### 2. To delete an object that is described in a configuration file:
         
         kubectl delete -f boot-pod.yaml
         kubectl delete -f boot-service.yaml
         
         
         $ kubectl delete -f boot-pod.yaml
         pod "boot-pod" deleted
         
         $ kubectl delete -f boot-service.yaml
         service "boot-service" deleted
         
         
         
        
##### 3. To get the running objects(Pod, Service, Deployment etc.):

         kubectl get pods
         kubectl get services
         kubectl get deployments
         
         $ kubectl get pods
         NAME                               READY   STATUS    RESTARTS   AGE
         boot-deployment-5576f5bd8b-24fg6   2/2     Running   0          55m
         boot-deployment-5576f5bd8b-7rbhc   2/2     Running   0          55m
         boot-deployment-5576f5bd8b-wbkkj   2/2     Running   0          55m

         $ kubectl get services
         NAME           TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
         boot-service   NodePort    10.104.226.197   <none>        8080:30813/TCP   2m26s
         kubernetes     ClusterIP   10.96.0.1        <none>        443/TCP          16d

         $ kubectl get deployments
         NAME              READY   UP-TO-DATE   AVAILABLE   AGE
         boot-deployment   3/3     3            3           71m



##### 4. To describe a running pod:

         kubectl describe pod boot-pod


##### 5. To get the logs of a running container:

         kubectl logs boot-pod springboot-app
         
         
##### 6. To create/update pods using Deployment object:

         kubectl apply -f boot-deployment.yaml
         
###### Deployment objects are like a template for pods.


##### 7. To see the ReplicaSet (rs) created by the Deployment:

         kubectl get rs
         
         $ kubectl get rs
         NAME                         DESIRED   CURRENT   READY   AGE
         boot-deployment-5576f5bd8b   2         2         1       22s
         boot-deployment-855b55459b   2         2         2       16m
       
       
       
##### 8. To see the Deployment object:

         kubectl get deployments
         
         $ kubectl get deployments
         NAME              READY   UP-TO-DATE   AVAILABLE   AGE
         boot-deployment   3/3     2            3           16m

         
         
##### 9. To see the labels automatically generated for each Pod:

         kubectl get pods --show-labels         
         
         $ kubectl get pods --show-labels 
         NAME                               READY   STATUS    RESTARTS   AGE   LABELS
         boot-deployment-5576f5bd8b-24fg6   2/2     Running   0          38m   component=web,pod-template-hash=5576f5bd8b
         boot-deployment-5576f5bd8b-7rbhc   2/2     Running   0          38m   component=web,pod-template-hash=5576f5bd8b
         boot-deployment-5576f5bd8b-wbkkj   2/2     Running   0          37m   component=web,pod-template-hash=5576f5bd8b
