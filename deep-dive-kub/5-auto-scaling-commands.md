# Auto-Scaling Commands


https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/9671606?start=0


- (In the first terminal)

    # since the latest minikube doesn't enable metrics-server by default
    ` minikube addons enable metrics-server  `

    ` kubectl apply -f ./wordpress-deployment.yaml `

    ` kubectl autoscale deployment wordpress --cpu-percent=50 --min=1 --max=5 `


- (In the other terminal)

    ` kubectl run -i --tty load-generator --image=busybox /bin/sh `

    ` while true; do wget -q -O- http://wordpress.default.svc.cluster.local; done `

- (In the first terminal)

    ` kubectl get hpa `


## Trouble Shooting

    -  In the other terminal where the load-generator is running, if it shows below errors


        ` / # while true ; do wget -q -O- http://wordpress.default.svc.cluster.local ; done
          wget: can't connect to remote host (10.XX.XXX.XXX): Network is unreachable
          wget: can't connect to remote host (10.XX.XXX.XXX): Network is unreachable
          wget: can't connect to remote host (10.XX.XXX.XXX): Connection timed out
          wget: can't connect to remote host (10.XX.XXX.XXX): Network is unreachable
          wget: can't connect to remote host (10.XX.XXX.XXX): Connection timed out `

    - Solution :

          -  replace ` http://wordpress.default.svc.cluster.local ` with the output of ` minikube service wordpress --url `


          - EX:

              ` while true ; do wget -q -O- http://192.168.99.100:32094 ; done `


## Related Q & A


https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4400548

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4838588
