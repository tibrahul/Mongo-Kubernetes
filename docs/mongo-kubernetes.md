
![Logo](https://github.com/tibrahul/Mongo-Kubernetes/blob/master/GeppettoIcon.png?raw=true"Logo")

# Kubernetes with Mongo<br/>
 In here we will see on how to deploy mongo with kubernetes with volumes for data backup.
 
# Content<br/>
 1. [Prerequisites](#prerequisites)
 1. [Mongo Installation](#mongo-installation)
 
 # Prerequisites
 [Install minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)<br/>
 [Install VM](https://www.virtualbox.org/wiki/Downloads)
 
 # Mongo Installation
 
 MongoDB is a cross-platform document-oriented database program. It is issued under the Server Side Public License version 
 
 1. which was submitted for OSI certification but later withdrawn in lieu of SSPL version 
 
 2. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemata.
 
## Setting up Mongo with Kubernetes
 
 Before start to create the service and deployment we need to start the minikube
 
      minikube start
      
 To check the status of the minikube 
 
      minikube status
  
 The above command is shown that minikube running successfully
 
      host: Running
      kubelet: Running
      apiserver: Running
      kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
      
Then write the file for deployment,service and secret. Here i write the file for sonarqube and postgres. 
 
Following file is used to create the volume for the mongo. So i used the object kind as a PersistentVolumeClaim.
 
1. [mongo-volume-claim.yaml](https://github.com/tibrahul/Mongo-Kubernetes/blob/master/docs/mongo-volume-claim.yaml)
 
         kubectl create -f mongo-volume-claim.yaml
       
  To list the persistent volumes, 
  
        kubectl get pv                                                                                                                                                                                                                                     
          NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM  
          pvc-07063cf6-042b-11e9-b3e2-080027f13b47   5Gi        RWO            Delete           Bound    default/mongo-data
    
          STORAGECLASS   REASON   AGE
          standard                1h

2. [Deployment.yaml](https://github.com/tibrahul/Mongo-Kubernetes/blob/master/docs/Deployment.yaml)
 
         kubectl create -f Deployment.yaml
         
         
   To list the deployment,
         
         kubectl get deployment
         
         NAME             DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
         mongo            1         1         1            1           2h

         
3. [Service.yaml](https://github.com/tibrahul/Mongo-Kubernetes/blob/master/docs/Service.yaml)
 
         kubectl create -f Service.yaml
         
 To list the service,
 
          kubectl get service
 
         NAME             TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)       AGE
         mongo            ClusterIP   10.103.113.26   <none>        27017/TCP      2h
         
Once you  created the service and the deployment you need to check on the Pod which will has been created for Mongo

You check by giving,

      kubectl get pod
     
         NAME                              READY   STATUS    RESTARTS   AGE
         mongo-fcddb8dfd-nq4p7             1/1     Running   0          2h
      
      
