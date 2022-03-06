# Setting up your lab environment

> **Note:** You can all take turns in doing different parts of this
> in the little teams you've created.

To start, we will create a folder to hold the lesson files.

```bash
mkdir deployment-demo && cd deployment-demo
```

## Create a Kubernetes Namespace

We will create and use a namespace so that everything we create in this
demo will be walled off and won't affect anything in the cluster.

This is something that will be very common to you when deploying applications
in the future, so for now, consider it a little walled-garden to play in.

The contents of the YAML below are in the file `namespace.yaml`

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: deployment-demo
  labels:
    apps: web-based
  annotations:
    type: demo
```

Use `kubectl` to create the namespace in the cluster you're connected to.

```bash
kubectl apply -f resources/namespace.yaml
```

[Click here to continue](./namespace-ideas.md)
