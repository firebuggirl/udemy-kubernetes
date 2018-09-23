# Install Kubectl and Minikube


` kubectl version `


## Minikube commands

` minikube start `///starts local 1 node cluster

` kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080 `


` kubectl expose deployment hello-minikube  --type=NodePort `


` kubectl get pod
 `


 ` curl $(minikube service hello-minikube --url) `


 ` kubectl delete deployment hello-minikube
 `

 ` minikube stop `
