# What is Kubernetes?

Kubernetes (K8s) is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications. It provides a framework for running distributed systems resiliently and allows for easy management of applications running across clusters of hosts.

## Key Features:
- **Automated container scheduling:** Ensures containers are automatically placed based on available resources and requirements.
- **Self-healing:** Restarts failed containers, replaces and reschedules containers when nodes die, and kills containers that don’t respond to your user-defined health checks.
- **Horizontal scaling:** Scales applications up or down based on demand, either manually or automatically.
- **Service discovery & load balancing:** Automatically exposes a container using a DNS name or through their own IP address, and load balances traffic.
- **Automated rollouts and rollbacks:** Gradually roll out changes to your application or configuration and roll back if something goes wrong.

---

# Kubernetes Architecture

Kubernetes has a **master-slave architecture** where the master components manage the worker nodes that run the containerized applications.

### Master Node Components:
**API Server:** Acts as the frontend for the Kubernetes control plane. It exposes the Kubernetes API. It manages the state of objects (Pods, Services, Deployments) defined in the YAML files.
**etcd:** A key-value store that stores all the data used to manage the cluster, it stores the cluster's state data, including the specifications of Pods, Services, and Deployments.
**Scheduler:** Responsible for assigning Pods to worker nodes based on resource requirements. Assigns the example-pod to a node with available resources.
**Controller Manager:** Ensures the cluster is in the desired state by managing controllers (such as the node controller, deployment controller).

### Worker Node Components::
**kubelet:** An agent that runs on each worker node. It communicates with the API server and ensures that containers are running in the Pod and ensures pod are healthy.
**kube-proxy:** Maintains network rules and allows network communication to your Pods from network sessions inside or outside of the cluster (route traffic to the appropriate Pods).
**Container Runtime:** Responsible for running containers (e.g., Docker, containerd, CRI-O). Executes the nginx:latest container within each Pod.

### High-Level Flow:
1. Users interact with the **API Server** to create resources (e.g., Pods, Services).
2. The **Scheduler** assigns the Pod to a node.
3. The **Controller Manager** ensures the desired state by adjusting the running instances.
4. The **kubelet** on the worker node ensures the Pod runs as intended.
5. The **kube-proxy** ensures network traffic is properly routed.

---

# How to Set Up a Kubernetes Cluster (Master & Worker Node)

### Prerequisites:
- Two or more machines with Linux (Ubuntu/CentOS).
- SSH access to all machines.
- Kubernetes and Docker installed on all machines.

### Step 1: Install Kubernetes Components on All Nodes
1. Install Docker.
2. Install Kubernetes components:
   ```bash
   sudo apt-get update
   sudo apt-get install -y apt-transport-https curl
   curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"
   sudo apt-get update
   sudo apt-get install -y kubelet kubeadm kubectl


### Key Concepts:
**Cluster:** A group of nodes.
**Node:** A machine (physical/virtual) where Kubernetes runs.
**Pod:** The smallest unit in Kubernetes, representing a running process.
**Service:** Provides a stable IP address and DNS name for a set of pods.
**Ingress:** Manages external access to the services.
**Namespace:** Logical partitioning of the cluster resources.
**Volumes:** Persistent storage for Pods.


### Kubernetes Resources:
**Deployments:** For managing stateless apps (like Nginx or web servers).
**StatefulSets:** For stateful applications (like databases).
**ConfigMaps/Secrets:** For configuration data and sensitive information.
**Persistent Volumes/Claims:** For storage management.
**ServiceAccount:** Provides identity for the application to interact with the Kubernetes API.
**Role:** Defines permissions for the Service Account.
**RoleBinding:** Binds the Role to the Service Account, allowing it to act based on the defined rules.
**Secret:** Stores the token generated for the Service Account, enabling the pod to authenticate.
**Deployment:** Manages the lifecycle and replicas of the application.
**Service:** Exposes the application to the network.