## Kubernetes Commands
Here are some essential Kubernetes commands for managing clusters, nodes, pods, services, and other resources.


### Basic Commands:

- **Get Cluster Info:**
  `kubectl cluster-info`

- **Get Nodes:**
  `kubectl get nodes`

- **Get Pods:**
  `kubectl get pods`

- **Get Services:**
  `kubectl get services`

- **Get Deployments:**
  `kubectl get deployments`

### Creating Resources:

- **Create a Pod:**
  `kubectl run nginx --image=nginx`

- **Create a Deployment:**
  `kubectl create deployment nginx --image=nginx`

- **Create a Service:**
  `kubectl expose deployment nginx --port=80 --target-port=80`

- **Apply Configuration from File:**
  `kubectl apply -f <filename>.yaml`

### Viewing and Describing Resources:

- **Describe a Node:**
  `kubectl describe node <node-name>`

- **Describe a Pod:**
  `kubectl describe pod <pod-name>`

- **Describe a Service:**
  `kubectl describe service <service-name>`

### Editing Resources:

- **Edit a Deployment:**
  `kubectl edit deployment <deployment-name>`

### Deleting Resources:

- **Delete a Pod:**
  `kubectl delete pod <pod-name>`

- **Delete a Deployment:**
  `kubectl delete deployment <deployment-name>`

- **Delete a Service:**
  `kubectl delete service <service-name>`

### Logs and Debugging:

- **Get Pod Logs:**
  `kubectl logs <pod-name>`

- **Get Logs for a Specific Container in a Pod:**
  `kubectl logs <pod-name> -c <container-name>`

- **Execute Command in Pod:**
  `kubectl exec -it <pod-name> -- /bin/bash`

- **Port Forwarding:**
  `kubectl port-forward <pod-name> <local-port>:<pod-port>`

### Scaling:

- **Scale a Deployment:**
  `kubectl scale deployment <deployment-name> --replicas=<number-of-replicas>`

### Namespace Management:

- **Create a Namespace:**
  `kubectl create namespace <namespace-name>`

- **Get Namespaces:**
  `kubectl get namespaces`

- **Use a Namespace:**
  `kubectl config set-context --current --namespace=<namespace-name>`

### Configuration Management:

- **Create ConfigMap:**
  `kubectl create configmap <configmap-name> --from-literal=<key>=<value>`

- **Create Secret:**
  `kubectl create secret generic <secret-name> --from-literal=<key>=<value>`