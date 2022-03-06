# What is a Service?

A Service is a way to expose an application running on a set of Pods as a network service.

Each Pod gets their own IP address and a single DNS name for a set of Pods.
Load balancing across them is provided by the Service.

Services are also useful because pods are ephemeral. So the service can keep track
of the IP addresses of the pods with `labels` matching the ones you've defined in the
`selector` section of your Service.

## Service Types

Services also need to be given a type - the default type is ClusterIP.

- **ClusterIP**: Exposes the Service on a cluster-internal IP. Choosing this value makes the Service only reachable from within the cluster.

- **NodePort**: Exposes the Service on each Node's IP at a static port (the NodePort). A ClusterIP Service, to which the NodePort Service routes, is automatically created. You'll be able to contact the NodePort Service, from outside the cluster, by requesting <NodeIP>:<NodePort>.

- **LoadBalancer**: Exposes the Service externally using a cloud provider's load balancer. NodePort and ClusterIP Services, to which the external load balancer routes, are automatically created.

- **ExternalName**: Maps the Service to the contents of the externalName field (e.g. foo.bar.example.com), by returning a CNAME record with its value. No proxying of any kind is set up.

Below is an example Service that fronts pods matching the `app: backend` label.

This service is one that returns a random colour and we will call it `colour-service`.

```yaml
kind: Service
apiVersion: v1
metadata:
  name: colour-service
  labels:
    app: backend
spec:
  selector:
    app: backend
  ports:
    - name: public
      protocol: TCP
      port: 80
      targetPort: public
```

### Official Documentation

[Kubernetes Services](https://kubernetes.io/docs/concepts/services-networking/service/)
