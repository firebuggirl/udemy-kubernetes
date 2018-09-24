# DNS & Service Discovery


- `DNS` -> translates names into IP addresses -> built into kubernetes -> configures kublets to tell individual containers to use the DNS service's IP to resolve DNS names


    - ` <my-servicename>.<my-namespace>.svc.cluster.local `

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/t/lecture/11291146?start=0

  -  syntax of the deployment files and kubectl commands:

      - Introduction to YAML: Creating a Kubernetes deployment:

        https://www.mirantis.com/blog/introduction-to-yaml-creating-a-kubernetes-deployment/

            - NEVER use tabs in a YAML file!!



        - `apiVersion:`

            - https://github.com/LevelUpEducation/kubernetes-demo/blob/master/Advanced%20Kubernetes%20Usage/DNS%20and%20Service%20Discovery/mysql-deployment.yaml#L15


            ` apiVersion: apps/v1beta2 ` # for versions before 1.8.0 use apps/v1beta1

        - `---` is used for separating documents. It allows us to place multiple things in a single file. '---' allows us placing them in a single file instead of creating separate documents for services, deployments, etc...

        - `kubectl create` vs `kubectl apply` :


            - `kubectl create` -> only for creating new deployments

            - `kubectl apply` -> used for both creating and updating deployments
