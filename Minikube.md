# Minikube

It runs on a VirtualBox or some other virtualization type.  
It runs Master and Worker processes on the same machine.  

Is it installed? Just run ``minikube version``  
Minikube has Kubectl as dependency, so it will use it.  

Is it running?  

``minikube status``

``minikube start``
``minikube stop``
``minikube delete`` what is this doing?


Minikube is used just to start/stop the cluster, all the operations will be done with kubectl.  