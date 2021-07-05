# create k8s cluster on my local mac
steps:
insatall docker
install virtual box
install kubectl
install minukube
start minukube
#deploy jenkins on k8s cluster steps:

# install helm
add bitnai repo (helm repo add bitnami https://charts.bitnami.com/bitnami)
run chart with cutom variables: helm install jenkins --set jenkinsUser=admin,jenkinsPassword=password,service.type=NodePort,service.port=8080,extraVolumes=/Users/eyal/.docker:/home/jenkins/.docker:rw bitnami/jenkins which set the service as NodePort instead of Load Balancer which is for cloud use and not to use with Minikube.
jenkins is now available at: http://192.168.99.100:31417 - ip of Minikube host and port assgined to jenkins service.

# steps to create DNS for jenkins we will need to use ingress. for that we will need to:

deploy ingress controller in the cluster (as nginx for example).
create ingress resource yaml file for the jenkins with the dns settings

# steps to create docker file with jenkins pipeline
created a pipeline that pulls the git repository and run the Dockerfile insidde the repo.
it craetes the docker image and pulls it to dockerhub using the credentials configuerd in the credentilas manager (in jenkins).

# monitoring solutions

* Promethous & Grafana - most pupolar, collect the metrics from the cluster using Prometheus and display them in Grafana.
* Heapster, influxDB and Grafana - Heapster collect the metrics, send the data over to influxDB, and Grafana for visualization.
* ELK - elasticsearch + kibana with a log shipper for example: fluentd.
* Datadog - deploy datadog as a deamon set in the cluster. dd agent will do the rest. - proprietary solution.
* Dynatrace - another proprietary apm solution. 
