# Kubernetes 

## What is Kubernetes? 

Kubernetes is an orchestration tool which helps manage containerised applications i.e applications made up of many Docker containers. 

Kubernetes can manage such applications in different types of environments e.g. physical machines, virtual machines, or cloud environments. 

what problems do orchestration tools solve? 

orchestration tools mean you don't need to write scripts to manage applications built up of multiple microservices (each being held in a container) across multpiple environments. 

What featres do orchestration tools offer? 

- High **availability** so no downtime 
- **scalability** by increasing or decreasing the number of running containers/pods based on traffic.
- **disaster recovery** by automatically replacing failed containers and rescheduling workloads to healthy nodes.

## Kuberenetes architecture - How it works in the background

You build an application 
applications have moved away from the monolithic approach to the microservice approach.
You containerise all the microservices using docker.
Each container is wrapped inside a pod. 
A pod is just an abstraction layer on top of the container.
docker takes the pods and mounts them onto a cluster.
a cluster is a space containing multiple servers AKA Nodes (physical, VM's etc.).
pods are distributed among the different servers/nodes. 
kubernetes can add resources (memory, gpu etc.) to a server/nodes when load increases.
kubernetes can add more pods of a microservice if traffic increases. 
kubernetes can move pods from one server/node to another is a server/node breaks. 

A cluster is made of three main components:

Control plane (AKA Master node) - decides what should run where. 
Contains a container holding the API server. Needed for clients to communicate with K8S cluster. 
Contains a container holding the 'controller manager'. Keeps track of whats going on in the cluster. 
Contains a container holding the 'scheduler'. Decides which worker node a new pod should be placed on based off available resources. 
Contains an etcd database. hold the current state of the cluster. 
always have a backup of your master node. 

kubernetes offers an out of the box virtual network - communication layer used by all nodes to communicate with one another. 

Worker nodes - nodes which actually run the processes. 
the worker nodes contain a "kubelet" which allows all nodes to communicate with one another. 
the worker nodes also contain the pods. 
worker nodes are usually allocated more resources compared to master node due to higher load 

pods, cluster, plane, nodes, jobs, images vs containers, 


services:
each pod is given a IP address to communicate with one another. 
pods are ephemiral which means pods die easily. 
when this happens a new pod is created in its place with a new IP.
The new IP is annoying as it means other pods need to be given this new IP. 
Instead of normal IP, kuberneted use what known as a 'service' which is a static IP Address which lives on even when a pod is replaced. 
you can create internal or external services depending on if you want the service accessable from external sources. 

ingress:
Ingress is a component in kuberneets which routes traffic to the correct service. 

instead of users accessing a enternal service like this: http://124.89.101.2:8080 (http://node-ip:service-port-number)

ingress allows users to access the service through something like this: https://my-app.com and routes it to http://124.89.101.2:8080 





## Main components on Kubernetes 
