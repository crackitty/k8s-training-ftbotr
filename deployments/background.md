# Background

Before we talk about Deployments, we need to take a step back and
look at how things were done in the past with typical server setups.

In the traditional setup we have servers that run our applications and
those servers had lots of tools and applications running on them in
order for them to work correctly. This was configured usually using
script. But scripts are prone to failure at any point in the script
and are unreliable.

Kubernetes takes a different approach to this and defines what they call
a `desired state` whereby Kubernetes will attempt to guarantee the
configuration you ask it for via what you have specified in the `deployment.yaml`
file.

We will look into this next.

[Continue](./deployment.md)
