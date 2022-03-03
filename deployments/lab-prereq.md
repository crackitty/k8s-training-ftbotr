# Settings to be done before the day of the lab (if possible)

The training will be hands on and entail the use of the following:

1. A terminal
2. An editor
3. A Kubernetes cluster

For the first two, we will recommend using VSCode since you will have the terminal
and editor available in the same environment but feel free to use a simple terminal
and it's built in `vi` or `nano` if you like.

If you don't have VSCode, you can [download it here](https://code.visualstudio.com/).

# Kubernetes Cluster

**Note:** If you have an available Kubernetes cluster you can use you can skip this.

If you are planning to do this on your local machine, then we suggest installing
`kind` which is a lightweight Kubernetes Cluster used for local development that
provides us with all we need for this demo.

You can install kind by following what is described in [this link](https://kind.sigs.k8s.io/docs/user/quick-start/#installation).

After that is done, simply run the following command and you have a single node cluster.

```bash
kind create cluster
```
