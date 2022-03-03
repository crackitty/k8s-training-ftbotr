# What should we do?

## Pre-training expectations

- Learners have laptops
- Learners have terminals
- Learners have access to a k8s cluster - kind on localhost if need be

## Prepared material that is given to the learners

- Definitions of the main topics
  - Kubernetes
  - kubectl
  - Pod
  - Deployment
  - Service
  - LoadBalancer Service
  - Replicaset
  - Use of labels in k8s
- Cheat-sheet of kubectl commands

## Define the Training Objectives

- Understand the difference between Docker and Kubernetes
- Understand what Pods, Deployments and Services are
- Understand why this suits a microservice architecture

## Overall concepts to be handled

- what is kubernetes and why is it different from docker
- brief overview of the architecture
- `kubectl` must be used
- logging into a cluster must be done
- Deploy a simple `Pod`
- Then talk about why this isn't enough
- Intro to what a `Deployment` is
- Write a `deployment` and show how it is sent to the k8s api on the master and across to the worker nodes
- Explain what happens in the deployment with a `Replicaset` being created
- Next we need to talk about how the applications in the pods can talk to eachother - each pod has a cluster ip
- We want to access the replicaset in a simpler way, so we use a `Service` that fronts all the pods with
  matching `labels`
- Show how this works in the diagram
- Next show how to expose one replicaset to the outside world using a `Service` of type `LoadBalancer`

## Next steps

Now I need to break this into presentation bits of no more than 5 minutes.

Interspersed will need to be ways for the learners to pair up and/or have some activities where they work together.

