# Kubernetes Overview

So, the first thing we want to understand is why are we using this thing called
Kubernetes? What's the big deal?

Well, that's a very big question, but a simplified way to look at this is to look
at your own application you want to make available.

## The past

In the traditional setup we have servers that run our applications and
those servers had lots of tools and applications running on them in
order for them to work correctly. This was configured usually using
script. But scripts are prone to failure at any point in the script
and are unreliable.

## The present

Kubernetes is an orchestration tool that allows you to run and manage
workloads.

It uses YAML to allow you to defines what they call the `desired state`
you would like whereby Kubernetes will try to guarantee that the
configuration you ask it for will be present in the cluster.

These manifests can appear quite complex at first, but they adhere to schemas
that are well defined and there is excellent documentation to help understand
how to use them.

Kubernetes also provides us with a lot more than this that will not be covered
in this training. Some of the things that Kubernetes will give us are:

- Portability of our infrastructure
- Multi-cloud cabability
- Better ecosystem for developers using devOps
- Very good fit for Microservice architectures
- Open source
- Battle-tested
- Market leader

## Kubectl

Kubernetes provides a command line tool that allows you, as a user, will use to
communicate with the cluster's control plane and the kubernetes API.

There's a lot you can do with kubectl and you can see what you can do by using
the official documentation site [here](https://kubernetes.io/docs/reference/kubectl/),
but for now, you can consider it the tool we will use to apply state changes to the
cluster via the command line.

[Click here to continue](./exercises/app-capabilities.md)
