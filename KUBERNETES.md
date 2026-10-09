KUBERNETES







Official definition of Kubernetes :

* Open source container orchestration tool
* Developed by Google
* Helps manage containerized applications in different deployment environments





Need for container orchestration tool :

* Trend from Monolith to Microservices
* Increased usage of containers
* Demand for a proper way of managing those hundreds of containers

&#x20;



What features do orchestration tools offer?

1\. High availability or no downtime

2\. Scalability or high performance

3\. Disaster recovery - backup and restore. 









MASTER Node :

API SERVER

Schedule

ETCD

Control Manager





Worker Node :

Kubelet

Kube-proxy

Container-runtime











* Kubernetes (often abbreviated as K8s) is a powerful container orchestration tool designed to manage thousands of containerized applications automatically. It handles essential operations like deployment, scaling, load balancing, and monitoring, ensuring your infrastructure remains highly available and efficient 



Kubernetes Architecture  :

* A Kubernetes cluster is composed of a Master Node (the control plane) and multiple Worker Nodes (where applications actually run).



* 1\. Master Node (The Brain):



* API Server : The front-end/reception area. It handles all requests from clients (UI or CLI), validates them, and coordinates communication.
* ETCD : A key-value database that stores the state of the cluster, including node information and availability.
* Scheduler : The manager that assigns Pods to specific worker nodes based on resource availability.
* Control Manager : Ensures the cluster's current state matches the desired state (e.g., replacing a failed pod)



* 2\. Worker Node (The Execution Area):



* Pod : The smallest deployable unit. Think of it as a hotel room where your containers (business logic, database) reside.
* Kubelet : An agent on each worker node that ensures containers are running and healthy, acting like 'room service' for the pods.
* Kube-proxy : Manages network connectivity and load balancing between pods to ensure they can talk to each other.
* Container Runtime : The software (like Docker) responsible for actually starting, stopping, or pausing the containers based on instructions from the Kubelet.

































































