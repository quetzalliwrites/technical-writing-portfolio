# The `kubectl debug` cheatsheet 

Welcome to your `kubectl debug` troubleshooting cheatsheet! 

The `kubectl` CLI uses the Kubernetes API to help you communicate with Kubernetes clusters (a group of computing machines that run containerized applications).

`Kubectl` offers various debug commands for diagnosing and resolving issues within your Kubernetes environment. 

The table below explains some useful `kubectl` commands to support you during debugging workflows. 


| Command                        | Description                                                                                  | 
|--------------------------------|----------------------------------------------------------------------------------------------|
| `kubectl get`    | Get a list of all available pods (a group of one or more containers) and their status.                     | 
| `kubectl logs`        | Retrieve the logs for a specific pod. Use this when you must review logs or debug a container.        |
| `kubectl exec`        | Explore a container and review its internal log files or configurations.                              |
| `kubectl debug`       | Create a pod copy that continues to run for troubleshooting, even if the container encounters errors. | 

The table below explains some `kubectl` flags you'll want to use with the above commands.

| Command          | Flags                            | Description                                             |
|------------------|----------------------------------|---------------------------------------------------------|
| `kubectl get`    | `pods --all-namespaces`          | Retrieve information about all pods from all namespaces (help organize/manage cluster resources). |
| `kubectl logs`   | `-c`                             | Specify the container within the pod to fetch logs from. |
|                  | `--all-pods`                     | Fetch logs from all pods in the namespace.           |
|                  | `--all-containers`               | Retrieve logs from all containers in a pod.            |
| `kubectl exec`   | `-c`                             | Specify in which container you want to execute a command. |
|                  | `--pod-running-timeout duration` | Set max waiting time for pod to be in running state before executing commands. |
| `kubectl debug`  | `-c`                             | Specify which container you want to debug.          |
|                  | `--copy-to string`               | Copy container files to a specified location on the host. |


## More resources
- A comprehensive [reference for using the `kubectl` debug command to manage your application](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#debug).
- A comprehensive [reference for understanding the `kubectl` debug command options](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_debug/).  
