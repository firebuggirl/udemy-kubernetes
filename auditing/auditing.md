# Auditing

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/9630340?start=0

- The `kube-apiserver` -> provides auditing functionality -> configured from outside the cluster


- 2 areas of concer:


    - `Audit Policy`

        - defines what should be logged in a yaml file -> an option passed tot he apiserver when it starts


    - the `Audit Backend`


        - export audit events to external storage

        - 2 backends:

              - `Logs` -> writes events to a disk

              - ` Webhooks` -> sends events to an external API/system


## EX: Set up simple Audit Policy to log all requests regarding Metadata


  -  Configure Minikube to log to a file on your machine

### Steps:


  - Stop Minikube (if running)

      - ` minikube stop `

  - Define an Audit Policy

  - Start Minikube with Audit policy defined and appropriate options

      - ` cp audit-policy.yaml ~/.minikube/addons/ `//mounted to the virtual machine that is running Minikube

      - `copy/paste bash script` into terminal

            - NOTE: `RBAC` = prerequisite (in shell script) to auditing + audit logs are saved here: `Path=/var/logs/audit.log`

      - ` kubectl get pods `//trigger an event that requires auditing


      - ` minikube ssh `

      - ` sudo bash `

      - ` cd /var/logs `

      - ` cat audit.log `

      - ` cat audit.log | jq . `//format data for readability

      - ` exit `

      - ` exit `

  - Repo: https://github.com/LevelUpEducation/kubernetes-demo/tree/master/Advanced%20Kubernetes%20Usage/Auditing






https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/11289804?start=0

## Trouble Shooting:

### Section 5, Lecture 59


  * Trouble Shooting:


    - If you hang running the script file on `Starting cluster components`... + and the error log in minikube says:


        ` failed to run Kubelet: unable to load bootstrap kubeconfig: stat /etc/kubernetes/bootstrap-kubelet.conf: no such file or director `

 * Solution:

    - an issue with `minikube 0.28`

    - uninstall  reinstall `minikube 0.25.2`


 * Related Q&A:


 https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4555676

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4471680
