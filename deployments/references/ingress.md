# What is an Ingress?

An Ingress is used to configure external access to the services in a
cluster, typically HTTP.

Ingresses also require an Ingress controller installed on the cluster.

## How it works

An Ingress exposes HTTP and HTTPS routes from outside the cluster to services
within the cluster. Traffic routing is controlled by rules defined on the Ingress
resource.

![Ingress](../images/ingress.png)

Below is a sample yaml file defining an ingress.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: demo-localhost
  namespace: default
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /$1
spec:
  ingressClassName: nginx
  rules:
  - host: frontend.localdev.me
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: frontend-service
            port:
              number: 80
```

In order for this to work you would have to get the IP address of the ingress and add it to
your local `/etc/hosts` file.

Do this by running

```bash
kubectl port-forward --namespace=ingress-nginx service/ingress-nginx-controller 8080:80
```

At this point you can test your ingress by opening this link in your browser

[http://frontend.localdev.me:8080/](http://frontend.localdev.me:8080/)

### Official Documentation

[Kubernetes Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)
[Kubernetes Ingress Controllers](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/)
[NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/deploy/#quick-start)
