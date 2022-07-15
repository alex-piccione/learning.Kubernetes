# miroK8s

https://www.youtube.com/watch?v=OTBzaU1-thg&ab_channel=CamilleRodriguez



## Install on VPS

It's Ubuntu so I'll use Snap.  
``snap install microk8s --classic``

Deploy Kubernetes dashboard with Grafana and InfluxDB.  
``microk8s.enable dashboard dns``

Get the auth token with ``token=$(microk8s kubectl -n kube-system get secret | grep default-token | cut -d " " -f1)``  
``(microk8s kubectl -n kube-system get secret``  


Does not work because needs permission and kubernetes still give the error about localhost:8080 not accessible. 