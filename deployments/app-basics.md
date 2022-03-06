# App Basics

We are going to deploy a very simple application that is composed of
a frontend and a backend.

They will need to talk to each other across the network and the frontend
will need to be accessible from outside the cluster.

To start, let's define a Pod that will run our frontend. Pods are the base
unit in Kubernetes for running a workload.

The minimum configuration for a Pod is as follows:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
  labels:
    app: frontend
spec:
  containers:
  - name: Frontend
    image: crackitty/demo-frontend:latest
```
