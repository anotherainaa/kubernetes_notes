
# Important concepts in Kubernetes

## Basic kubernetes components mental model

- kubectl
  - the "controller"
  - analogy: the president that gives instructions to the general(master node) that gives instructions to the soldiers(Worker Node)
- minikube
  - for testing k8s locally
  - everything is in a single node? TODO
- Master Node
  - have 4 componenets: apiServer, etcd (the brain / data), TODO , TODO
- Worker Node
  - the nodes that will hold pods
  - can contain multiple pods

- Pods
  - an abstraction over containers which contains the apps etc
  - we don't need to create pods manually, k8s will handle it
- Deployment
  - an abstraction that handles the creation of pods
  - we can create a deployment by cli
  - or we can apply the configuration from a yaml file
- ReplicaSet
  - created by deployment based on how many replicas of the same pod we want
  - e.g 5 replicas of the application
- Service
  - pods are ephemeral, therefore the IP will change again and again when they go down
  - to make the IPs static, we use service

### Common services
- LoadBalancer
- NodePort
- TODO

- nginx ingress (for loadbalancing)
  - ingress resource needs to be paired with ingress controller.
  - controller - loadbalancing related stuff
  - resource - defines the rules we need for our app

## Other concepts to take note of
- ConfigMap
- StatefulSet - for managing stateful things in k8s e.g databases. because databases need to persist data and can't just go down like pods.
- ECS vs EKS
  - While ECS doesn't know anything about k8s, the concept of tasks can be compared to pods
  - we run containers in tasks vs we run containers in pods


### Useful basic CLI commands

- `kubectl delete [resource] [name]`
- `kubectl apply -f [filename]`
- `kubectl get [resource] [name]`
  - Useful options: `all`, `-n` for namespace
- `kubectl describe [resource] [name]`

__Namespacing__
- to use namespace, use the flag `-n` and add the name space
- why do we use namspace?
  - to organize our pods by category so that it's easier to manage and maintain
  - to avoid clashing of project names if two teams use the same project for different purposes

- `minikube start --vm-driver=hyperkit` - We can also set user config to change default hypervisor
- `minikube pause`
- `minikube delete`

## Questions that might be helpful in the future to look into
- deeper dive into config files
- maybe some notes on how to read documentation, if there is anything worth noting
