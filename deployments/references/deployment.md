# What is a Deployment?

A deployment provides declarative updates for Pods and Replicasets

You use a deployment yaml to describe a desired state and the Deployment controller changes
the actual state to the desired state at a controlled rate.

## Sample YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

If the above were saved to the file `demo-dply.yaml` you would run the following to
create it.

Note the `-n deployment-demo` at the end - this tells Kubernetes to
create the deployment in the `deployment-demo` namespace.

```bash
kubectl create -f ./demo-dply.yaml -n deployment-demo
```

## Important sections

### `metadata`

In the `metadata` section we have the deployment name and (here) one label called app which
will be used to map some meaning your company has to this deployment - in this case, the `app: nginx`

### `spec: selector`

The selector is used to map the labels that match the pods for this deployment to manage.

### `spec: template`

The template section contains all the configuration required to create a pod for this deployment, as
such, the labels in the metadata will match those defined in the selector.

### Official Documentation

[Kubernetes Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
