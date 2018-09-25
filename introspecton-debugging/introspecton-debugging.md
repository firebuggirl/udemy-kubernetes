# Application Introspection and Debugging


https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application-introspection/



- Use a Deployment to create two pods:


      - ` kubectl create -f nginx-with-request.yaml `


      - ` kubectl get pods `


      - ` kubectl describe pod <pod-name> `

## Example: debugging Pending Pods

    - ` kubectl describe pod <pod-name> `

    - ` kubectl get events `

          - ..events are `namespaced` + persisted in `etcd`. ...if you’re interested in events for some namespaced object need to explicitly provide a namespace to the command:


              - ` kubectl get events --namespace=my-namespace `

              - to see events from all namespaces add `--all-namespaces` argument

    - `  kubectl get pod <pod-name> -o yaml `// get all of the information the system has about the Pod


## Example: debugging a down/unreachable node

    - ` kubectl describe node `

    - ` kubectl get node -o yaml  `


    - ` kubectl get nodes `


    - ` kubectl describe node <node-name> `

    - ` kubectl get node <node-name> -o yaml `
