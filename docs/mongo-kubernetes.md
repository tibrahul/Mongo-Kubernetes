
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
 
## Setting up SonarQube with Kubernetes
 
 Before start to create the service and deployment we need to start the minikube
 
      minikube start
      
 To check the status of the minikube 
 
      minikube status
  
 The above command is shown that minikube running successfully
 
      host: Running
      kubelet: Running
      apiserver: Running
      kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
