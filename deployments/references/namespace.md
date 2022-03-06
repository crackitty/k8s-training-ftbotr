# What is a Namespace?

In Kubernetes, namespaces provides a mechanism for isolating groups of resources
within a single cluster. Names of resources need to be unique within a namespace,
but not across namespaces.

## Sample YAML

Below is a sample yaml needed to create a Namespace.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: demo-namespace
```

If the above were saved to the file `demo-ns.yaml` you would run the following to
create it.

```bash
kubectl create -f ./demo-ns.yaml
```

Alternatively, you can do it just using `kubectl`

```bash
kubectl create namespace demo-namespace
```

### Official Documentation

[Kubernetes Namespaces](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)
