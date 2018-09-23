# Deploy MongoDB w/ Kubernetes

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/9630320?start=0

    - ` minikube start`

    - ` kubectl run mongo-exercise-1 --image=mongo --port=27017 `

    - ` kubectl scale --replicas=4 deployment/mongo-exercise-1 `

    - ` kubectl describe deployment mongo-exercise-1 `

    - ` kubectl delete deployment mongo-exercise-1 `




- OR


    - w/ `deployment.yml` + `service.yml`:


          - ` kubectl apply -f deployment.yml `


          -  ` kubectl apply -f service.yml `

          - `  kubectl describe deployment mongodb-kubernetes `

          - ` kubectl delete deployment mongodb-kubernetes `



 - OR

     - Use `Helm` package manager
