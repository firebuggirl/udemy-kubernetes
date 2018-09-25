# Logging Architecture

https://kubernetes.io/docs/concepts/cluster-administration/logging/

  - useful for debugging problems and monitoring cluster activity

  - `cluster-level-logging` -> logs should have a separate storage and lifecycle independent of nodes, pods, or containers


        - requires a separate backend to store, analyze, and query logs...no native storage solution for log data, but you can integrate many existing logging solutions


## Basic logging in Kubernetes

    - outputs data to the standard output stream

    - EX: pod specification with a container that writes some text to standard output once per second

      - ` counter-pod.yaml `

      - ` kubectl create -f counter-pod.yaml `

      - ` kubectl logs counter `

            - add `--previous` flag to retrieve logs from a previous instantiation of a container

      - kubectl logs `documentation`:

            - If a pod has multiple containers, should specify which container’s logs you want to access by appending a container name to the command

            - ` https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#logs `



## Logging at the node level


    - Everything a containerized application writes to `stdout` and `stderr` is handled and redirected somewhere by a container engine.

    - `log rotation`:

        - so that logs don’t consume all available storage on the node

        - Kubernetes currently is not responsible for rotating logs

        - use a `deployment tool`

            - deploy w/ `kube-up.sh` script w/ a `logrotate` tool configured to run each hour

                  - used for COS image on GCP?

            - can also set up a container runtime to rotate application’s logs automatically, e.g. by using Docker’s `log-opt`

                  - In both cases, default rotation takes place when log file exceeds `10MB`

        - if external system has performed the rotation, only the contents of the latest log file will be available through `kubectl logs`

              - if `10MB` file, logrotate rotates + creates two files, one 10MB + one empty, kubectl logs will return an empty response

## System component logs


    - Two types of system components:


          - run `in` container

                - ` Kubernetes scheduler `

                - ` kube-proxy `


                    - write to `/var/log directory`

          - does `not` run in container

                - `kubelet`

                - `container runtime` //for example Docker

                    - machines w/ `systemd`, the kubelet and container runtime write to `journald`

                    -  If !systemd , they write to .log files in the `/var/log` directory
