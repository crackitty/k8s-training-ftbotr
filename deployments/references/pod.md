# What is a Pod?

Pods are the smallest deployable units of computing that you can
create and manage in Kubernetes.

It's a group of one or more containers with shared storage and
network resources, and a spec for how to run the containers.

Pods are generally not created directly but instead it is good
practive to have workload resources create them for you.

Typically these will be Deployments or Jobs. If you need to track
state, then you would use StatefulSet resources.

## Sample YAML

Below is a sample yaml for a single Pod.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

If the above were saved to the file `demo-pod.yaml` you would run the following to
create it.

Note the `-n deployment-demo` at the end - this tells Kubernetes to
create the deployment in the `deployment-demo` namespace.

```bash
kubectl create -f ./demo-pod.yaml -n deployment-demo
```

### Official Documentation

[Kubernetes Pods](https://kubernetes.io/docs/concepts/workloads/pods/)
