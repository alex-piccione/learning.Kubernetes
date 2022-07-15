# Kubectl on remote server

I connected to a local pc with Ubuntu installed trough SSH.  
I installed Kubernets with ``apt install kubernetes``  
Then I installed kubectl (It required snap, the Canonical package, but that's it).  
Docker is installed and has no images and no containers.  

``kubetcl version`` shows that Kubernetes Client 1.24.1 is installed.   
Not the server?  

Tried to run ``kubectl describe services`` and got:
> The connection to the server localhost:8080 was refused - did you specify the right host or port?

Tried to run ``kubetcl create deployment ...`` and got this error:
> ... tcp 127.0.0.1:8080: connect: connection refused

This error is mentioned here: <https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/>

Follow these to install Kubernetes Cluster:
https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
https://kubernetes.io/docs/setup/
https://kubernetes.io/releases/download/
https://kubernetes.io/releases/download/
curl -Ls "https://sbom.k8s.io/$(curl -Ls https://dl.k8s.io/release/latest.txt)/release"  | awk '/PackageName: k8s.gcr.io\// {print $2}'