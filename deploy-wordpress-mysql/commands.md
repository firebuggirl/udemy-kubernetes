# Example: Deploying WordPress and MySQL with Persistent Volumes

https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/


      - Create PersistentVolumeClaims and PersistentVolumes

      - Create a Secret

      - Deploy MySQL

      - Deploy WordPress

      - Clean up


  - Many cluster environments have a default StorageClass installed. When a StorageClass is not specified in the PersistentVolumeClaim, the cluster’s default StorageClass is used instead.

      - In local clusters, the default StorageClass uses the `hostPath` provisioner. hostPath volumes are only suitable for development and testing. With hostPath volumes, your data lives in `/tmp` on the node the Pod is scheduled onto and does not move between nodes. If a Pod dies and gets scheduled to another node in the cluster, or the node is rebooted, the data is lost.


  - Start Minikube:

      - ` minikube start `

  - Create a `secret`:

      - ` kubectl create secret generic mysql-pass --from-literal=password=YOUR_PASSWORD `

      - `  kubectl get secrets `

  - Delete a secret:

      ` kubectl delete secret <secret-name> `


## Deploy MySQL


    - MySQL container mounts the PersistentVolume at `/var/lib/mysql`

    - `MYSQL_ROOT_PASSWORD` environment variable sets the database password from the `Secret`


    - ` kubectl create -f mysql-deployment.yaml `


    - Verify that a PersistentVolume got dynamically provisioned...can take up to a few minutes

          - `  kubectl get pvc `

    - Verify that the Pod is running

          - ` kubectl get pods `



## Deploy WordPress

    - `wordpress.deployment.yml`

            - has `PVC for persistent storage` and a `Secret` for the password

            - `type: LoadBalancer` -> exposes WordPress to traffic from outside of the cluster

                  -  -> allows for use of external LoadBalancer -> `elastic load balancing service`(provided by AWS w/external IP address...a pubic and 'usually' static IP Address...varies by provider)

                  - in `Minikube` -> `LoadBalancer` merely functions on a random port on your machine for testing purposes





    - ` kubectl create -f wordpress-deployment.yaml `


    - Verify `PVC` (PersistentVolume):


        - ` kubectl get pvc `


    - Verify that the Service is running:


        - ` kubectl get services wordpress `

                - Minikube can only expose Services through `NodePort`. The EXTERNAL-IP is always pending.


        - Get IP:


              - `  minikube service wordpress --url `


              - ` http://192.168.99.100:30430 `


              -  NOTE: Either install WordPress by creating a username and password or delete your instance to prevent prevent another user from finding this instance and serving up malicious content!!!!!!!


## Clean up


    - ` kubectl delete secret mysql-pass `


    -  delete all `Deployments` and `Services`:


          - `  kubectl delete deployment -l app=wordpress  `


          - ` kubectl delete service -l app=wordpress `


    - delete the `PersistentVolumeClaims` :


          - `  kubectl delete pvc -l app=wordpress `



## NOTE:


    - From the docs:

        - Not suitable for production use cases! Check out `WordPress Helm Chart` for deploying WordPress in production.
