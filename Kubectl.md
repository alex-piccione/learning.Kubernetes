# kubectl

When I installed minikube and started it I got this message:
"kubectl is now configured to use 'minikube' cluster and 'default' namespace by default"

That means if I want to interact with Google Cloud Platform I need to change that.  
``kubectl`` command shows all the available commands but none of them seems to indicate which cluster and namespace I'm working on.  

``kubectl config get-clusters``:
- docker-desktop
- minikube

``kubectl config get-context``: 
| Current | Name           | Cluster        | Authinfo       | Namespace
| ---     | ---            | ---            | ---            | ---
| *       | docker-desktop | docker-desktop | docker-desktop |  
|         | minikube       | minikube       | minikube       | default 

``kubectl config use-context minikube`` will switch the current context.  

## Create Pod

You don't create Pods. You crate deployment that manage pods through replicaset.

## Commands

``kubectl create deployment nginx-1 --image=nginx``
``kubectl get deployment``
``kubectl delete deployment {deployment name}``
``kubectl get pod``
``kubecttl get replicaset``

``kubectl edit deployment nginx-1``

``kubectl logs <pod name>``

``kubectl apply -f <file>`` create and update components

``kubectl exec -it <pod name> -- bin/bash``

``kubectl config view``

List namespaces: ``kubectl get namespaces``

What is the current namespace? ``kubectl config current-context  ``

``kubectl config current-context``  returns "minikube" after I installed it.


``kubectl get componentstatuses``