# Learning Kubernetes

Kubernetes study  
Based on "Kubernetes Up & Runing" book  
<http://bit.ly/kubernetesUR_2e>  
<https://github.com/kubernetes-up-and-running>  

Youtube - [Kubernetes in 4 hours](https://www.youtube.com/watch?v=X48VuDVv0do&ab_channel=TechWorldwithNana)  
  
Pluralsight - Getting started with Kubernetes (by Nigel Poulton):
https://app.pluralsight.com/course-player?courseId=3794d6de-7050-40ae-8e10-d245efeb7a0c


# What I learned

- What are Pods, Services, Ingress, 
- How to store secrets

## Components
- Node 
  It contains Pods.
- Pod 
  (abstraction over container) Usually a Pod runs a single application in it.
  It has an assigned internal IP.
  When die and is recreated it can get a difefrent IP. 
- Services
  Permanent IP address linked to the Pod. It does not share its lyfecicle with Pod.
  Can be internal or external (exposed to the outside).
  It serves also as load balancer.
- Ingress
  It's another component that exposes the URL ``<my-node>:<service-IP>`` to point over an external service as http://my=app.com  
- Secrets
- Volumes  
  
[1][images/Kubernetes components 01.png]

## ConfigMap & Secret
- ConfigMap is external to the nodes and is used to store configuration data (stored in plain format).  
- Secret: used to store credentials and other secret-data (stored as base64).
<!> Security mechanism is not setup by default.

## Deployments
- Deployment
  (abstraction of Pod)
  It's a blueprint of the Pod. Specify number of replicas.
- StatefulSet
  It's like deployment but it is for stateful application and Databases.
  It synchronizes read/writes to avoid database inconsistencies.
  Note easy to use.

## Cluster
Each Kubernetes Node should have a container runtime, kubelet and Kube Proxy that redirect communication to right Service.  
It will preser services on the same node to avoid unnecessary delay.  

MasterNode has this services to accomplish its tasks:
- API Server: to interact with the kubernetes cluster
- Scheduler: to schedule a new Pod. It will choose the better node for the job.
- Controller manager: detect state changes (like crash of Pods) and communicate with Scheduler
- etcd: (key-value) store for the cluster data (distributed with other master nodes)

## Data store
- Volumes
  Attach a disk, local or remote, to the kubernetes cluster.

# Exercises/Practicing
## Example 1

Docker image with Node.js and Express

## Example 2, 3
Well.. I don't remember.

## Example 4, 5
https://www.youtube.com/watch?v=X48VuDVv0do&ab_channel=TechWorldwithNana
