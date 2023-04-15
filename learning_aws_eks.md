# AWS EKS

## Some stuff I learned:

- to use EKS, first create a cluster.
- We can use AWS dashboard to do everything on the website which can be easier when getting to know things for the first time.
- use `eksctl` to simplify the process of creating a cluster
  - we can define the number of nodes, region and create a file to define resources needed
  - it also helps with beginners learning as it takes care of all required IAM policies and security groups as well

`eksctl`
- `eksctl create cluster`
  - pass in arguments such as `--name [kluster name]` `version [k8s version]` `--region [aws region]` etc
- `eksctl delete cluster --region [region] --name [cluster name]`

#### How to get `kubectl` to work with EKS cluster?
- set the `config` file in `/users/.kube` folder
- we can use AWS CLI to get it to create the config file for us. TODO: add CLI command

#### How to use `kubectl` with multiple clusters?
- TODO

#### Nginx ingress
- use the manifest provided by `nginx ingress` team
- note that there are two versions of nginx ingress, one maintained by k8s team, and one by nginx team.
- the default manifest will create an AWS network load balancer. TODO: maybe can elaborate more here and what it entails
- to terminate TLS on the load balancer side, check documentation.

## Questions that might be helpful in the future to look into
- loadbalancer and static ips?
- external dns?

