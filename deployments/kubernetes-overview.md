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

Kubernetes takes a different approach to this and defines what they call
a `desired state` whereby Kubernetes will attempt to guarantee the
configuration you ask it for via YAML defined manifests (configuration files).
These manifests can appear quite complex at first, but they adhere to schemas
that are well defined and there is excellent documentation to help understand
how to use them.

[Click here to continue](./exercises/app-capabilities.md)
