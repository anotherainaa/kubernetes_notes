### How to manually set up kubernetes on AWS?
- Create nodes for master node
- create worker nodes
- set up the traffic rules for API server, scheduler, controller manager, etcd
- TODO

### What etcd stores?
- distributed reliable store
- k8s configurations and manifest and state
- each componenets has different states
- e.g deployments revision, replicas?

### What is not in etcd?
- Application data is not stored in it.


### How to backup etcd and restore?
- use etcdctl
- install etc-client
-


### How to access a cluster using REST api with kubectl proxy
- check location, kubectl config view
- locating and authenticating
- curl, wget, browser
- how do we provide credentials and cluster location
- `kubectl proxy --port=8080` - acts as a reverse proxy
  - create a reverse procy on port 8080
- then we can curl this API endpoint of kubernets
- simple way to access kubernetes endpoints.
- we can get the services and default namespaces etc
- second way is without kubectl proxy
- we must pass the authentication data to the client - must belong to an authenticated user in the cluster
- write a script that access the endpoint and cleans up services etc that are not in use
- executed the script as a user with limited permissions
  - create service account
  - with role and rolebinding


### How does k8s cluster upgrade works?
- have more than 1 control plane node / master node
- when one node is being upgraded the other nodes are running
- down time is not necessary for upgrading k8s version

### What are we upgrading when upgrading k8s versions?
- apiserver
- controller manager
- scheduler
- kubelet
- kube proxy
- kubectl
- etcs, coredns
- weave-net???

### Should all componenets have the same versions?
- kube API server must have a later version than others.
  - 1 version earlier
  - 2 version earlier
- it makes sense to upgrate to the same version. unless a specific reason not to

### How to upgrade the components?
- Use `kubeadm` tool
- `kubeadm upgrade apply 1.21.0`
  - doesn't manage kubelet and kubectl
- clear the node of all the pods, drain nodes to remove all pods
- upgrade kubelete and kubectl

### How to upgrade Worker Nodes
1 - upgrade kubadm
2- executed kubeadm to upgrade all kubelete configuration
3 - drain the node
  - pods will be reschedule on other nodes
4 - upgrade kubelete
5 - change worker node back to schedulable
- upgrade everything one by one
- should not have diwn time during this update

### How do you drain nodes?
- marked unschedulable
- evict all nodes
- cordon vs uncordon command

### When and how often should you upgrade?
- when there is a fix in later versions.
- keep cluster up to date.
- k8s supports up to recent 3 versions.
  - upgrade one version at a time based on when the support will be deprecated

### How can we work with multiple clusters more easily?
- Use cluster context / kube context

### How can we manage certificate management in Kubernetes?
- use kubeadm
- we can also work with the lower level abstraction openssl, but kubeadm makes it easier to renew everything etc

