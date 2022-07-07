# Stop all the containers in Docker

I have plenty of Containers running in Docker named "k8s_POD...", "k8s_etcd_..." etcetera.  
They are consuming a lot of resources.  
Stopping or deleting the container has no effect because it is recreated.  

What should I stop?
- Services
What services are running?
``kubectl service list``  NO

How to List deployments?
  ``kubectl get deployments``

Stop minikube?
``minikube stop``
Error:
> PS C:\sources\learning\learning.Kubernetes> minikube stop
> E0617 14:06:50.730688   23528 daemonize_windows.go:39] error terminating scheduled stop for profile minikube: stopping schedule-stop service for profile minikube: NewSession: new client: new client: Error creating new ssh host from driver: Error getting ssh port for driver: get ssh host-port: get port 22 for "minikube": docker container inspect -f "'{{(index (index .NetworkSettings.Ports "22/tcp") 0).HostPort}}'" minikube: exit status 1
> stdout:
> ...
> Template parsing error: template: :1:4: executing "" at <index (index .NetworkSettings.Ports "22/tcp") 0>: error calling index: reflect: slice index out of range


``kubectl config get-contexts``
> CURRENT   NAME             CLUSTER          AUTHINFO         NAMESPACE
> *         docker-desktop   docker-desktop   docker-desktop

``kubectl config current-context``: 
> docker-desktop

``kubectl get pods``
> No resources found in default namespace.

Where the hell are all the pods ???

``kubectl get namespaces``
> NAME              STATUS   AGE
> default           Active   56m
> kube-node-lease   Active   56m
> kube-public       Active   56m
> kube-system       Active   56m

If "default" namespace has no resources... where the hell are all the pods ???


``kubectl get pods -n <namespace>``

``kubectl get pods -n default``         : No resources found in default namespace.
``kubectl get pods -n kube-node-lease`` : No resources found in kube-node-lease namespace.
``kubectl get pods -n kube-public``     : No resources found in kube-public namespace.
``kubectl get pods -n kube-system``     :
> NAME                                     READY   STATUS    RESTARTS        AGE
> coredns-6d4b75cb6d-2l8lc                 1/1     Running   2 (20m ago)     61m
> coredns-6d4b75cb6d-mtmdb                 1/1     Running   2 (20m ago)     61m
> etcd-docker-desktop                      1/1     Running   26 (20m ago)    61m
> kube-apiserver-docker-desktop            1/1     Running   25 (20m ago)    61m
> kube-controller-manager-docker-desktop   1/1     Running   28 (20m ago)    61m
> kube-proxy-crvt5                         1/1     Running   2 (20m ago)     61m
> kube-scheduler-docker-desktop            1/1     Running   28 (20m ago)    61m
> storage-provisioner                      1/1     Running   2 (20m ago)     61m
> vpnkit-controller                        1/1     Running   4 (2m12s ago)   61m


switch to that context/namespace:
``kubectl config set-context --current --namespace=kube-system`` 
> Context "docker-desktop" modified.

Now ``kubectl get pods`` returns the pods list!  

``kubectl get deployments``
> NAME      READY   UP-TO-DATE   AVAILABLE   AGE
> coredns   2/2     2            2           65m


``kubectl get deploy -A``
Find all the deployment across all the namespaces


Delete the deployment:
``kubectl delete deploy coredns -n kube-system``