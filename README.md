# create k8s cluster on my local mac
steps:
1. insatall docker
2. install virtual box
3. install kubectl
4. install minukube
5. start minukube 

#deploy jenkins on k8s cluster
steps:
1. install helm
2. add bitnai repo (helm repo add bitnami https://charts.bitnami.com/bitnami)
3. run chart with cutom variables: helm install jenkins --set jenkinsUser=admin,jenkinsPassword=password,service.type=NodePort,service.port=8080 bitnami/jenkins
   which set the service as NodePort instead of Load Balancer which is for cloud use and not to use with Minikube. 
4. jenkins is now available at: http://192.168.99.100:31417 - ip of Minikube host and port assgined to jenkins service.

#steps to create DNS for jenkins
we will need to use ingress. for that we will need to: 
1. deploy ingress controller in the cluster (as nginx for example).
2. create ingress resource yaml file for the jenkins with the dns settings

## steps to create docker file with jenkins pipeline

##monitoring
with promethous & grafana

