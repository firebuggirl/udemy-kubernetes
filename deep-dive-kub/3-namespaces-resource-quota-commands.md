https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/9671576?start=0


      ` kubectl create namespace <namespace name> `

      ` kubectl get namespace `

      ` kubectl create namespace cpu-limited-tomcat `

      ` kubectl create -f ./cpu-limits.yaml —namespace=cpu-limited-tomcat ` (from the GitHub repo directory for this lecture)


      ` kubectl apply -f ./tomcat-deployment.yaml —namespace=cpu-limited-tomcat ` (from the GitHub repo directory for this lecture)


      ` kubectl describe deployment tomcat-deployment —namespace=cpu-limited-tomcat `
