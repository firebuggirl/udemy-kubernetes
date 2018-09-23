# Web Interface Commands

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/9671560?start=0


` kubectl proxy
 `


 ` kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
 `



## Troubleshooting


- When trying to access the web UI through the serving proxy, It only navigates to `show all api paths and not the UI`.


` localhost:8001/ui `


## Solution:


    - This is an known issue of the current minikube, tracked on https://github.com/kubernetes/minikube/issues/3041

    - To walk round, you are still able to access the minikube dashboard by running:


      ` minikube dashboard `


      - Or using


      ` http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy `



### Related Q&A:


    - https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4393590

    - https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4812944
