# Deployments - Prereqs for the training

## Things you'll need

- Some paper (A4 if you have it)
- Some post-it notes
- Some pens - different colours if you have them
- if you have a white-board you can use that instead

## Let's make it a little more social

If you're not doing this in a solo setting. I'd like you to pair up
for this part of the training so that you can chat and talk some
things though from each others perspective.

So form little pairs, or even a three if you're an odd number so
that nobody is on their own.

## Settings to be done before the day of the lab (if possible)

The training will be hands on and entail the use of the following:

1. A terminal
2. An editor
3. A Kubernetes cluster

For the first two, we will recommend using VSCode since you will have the terminal
and editor available in the same environment but feel free to use a simple terminal
and it's built in `vi` or `nano` if you like.

If you don't have VSCode, you can [download it here](https://code.visualstudio.com/).

## Getting a Kubernetes Cluster

**Note:** If you have an available Kubernetes cluster you can use you can skip this.

If you are planning to do this on your local machine, then we suggest installing
`kind` which is a lightweight Kubernetes Cluster used for local development that
provides us with all we need for this demo.

You can install kind by following what is described in [this link](https://kind.sigs.k8s.io/docs/user/quick-start/#installation).

After that is done, run the following command and you have a single node cluster with some custom
config that allows the local host to make requests to the ingress controller over ports 80/443 and
also configure it to only allow the ingress controller to run on specific nodes matching the label
selector.

Don't worry about this for now - it's just a way to get a basic cluster running.

```bash
cat <<EOF | kind create cluster --config=-
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  extraPortMappings:
  - containerPort: 30080
    hostPort: 30080
EOF
```

We will make one addition to the local cluster - we need an Ingress Controller.

This is so that we can call into the cluster from outside and test our setup.

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

We then need to wait until the ingress controller is ready to accept requests - so
run the following to ensure this. If it results in a failure, just run it again until
you get `condition met`.

```bash
kubectl wait --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=90s
```

## Load Balancer for Kind

Installing metallb using default manifests

### Create the metallb namespace

```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/namespace.yaml
```

### Apply metallb manifest

```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/master/manifests/metallb.yaml
```

Wait for metallb pods to run

```bash
kubectl get pods -n metallb-system --watch
```

Setup address pool used by Load Balancers

```bash
docker network inspect -f '{{.IPAM.Config}}' kind
```

Create the ConfigMap

```bash
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: ConfigMap
metadata:
  namespace: metallb-system
  name: config
data:
  config: |
    address-pools:
    - name: default
      protocol: layer2
      addresses:
      - 172.19.255.200-172.19.255.250
EOF
```

[Click here to continue](./README.md)
