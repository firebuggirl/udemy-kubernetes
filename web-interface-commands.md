# Web Interface Commands

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/9671560?start=0


- ` Dashboard UI `

    - runs directly on `masters`

` minikube start `


 ` kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
 `//  services "kubernetes-dashboard" already exists

 ` kubectl proxy
`


` http://localhost:8000/ui `


## Troubleshooting


- When trying to access the web UI through the serving proxy, It only navigates to `show all api paths and not the UI`.


      ` http://127.0.0.1:8001/ `


## Solution:


    - This is an known issue of the current minikube, tracked on https://github.com/kubernetes/minikube/issues/3041

    - To walk round, you are still able to access the minikube dashboard by running:


      ` minikube dashboard `


      - Or using


      ` http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy `



### Related Q&A:


    - https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4393590

    - https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4812944
