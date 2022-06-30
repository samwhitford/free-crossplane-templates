[![Twitter Follow](https://img.shields.io/twitter/follow/can_o_spam.svg?style=social&label=Follow)](https://twitter.com/intent/follow?screen_name=can_o_spam)

# free-crossplane-templates
A place for me to share Crossplane templates that I've built that might help to serve others

# What is Crossplane?
![Crossplane](docs/images/crossplane_banner.png)

Crossplane is an open source Kubernetes add-on that transforms your cluster into a universal control plane. Crossplane enables platform teams to assemble infrastructure from multiple vendors, and expose higher level self-service APIs for application teams to consume, without having to write any code.

Crossplane extends your Kubernetes cluster to support orchestrating any infrastructure or managed service. Compose Crossplane’s granular resources into higher level abstractions that can be versioned, managed, deployed and consumed using your favorite tools and existing processes. [Install Crossplane](https://crossplane.io/docs/v1.8/getting-started/install-configure.html) into any Kubernetes cluster to get started.

Crossplane is a [Cloud Native Compute Foundation](https://www.cncf.io/) project.

# What is in this repository
This repository will contain items created by Sam Whitford for use in conjunction with Crossplane to describe cloud infrastructure using Crossplane.
The usual construction of these items will be:
1. Composite Resource Definition (XRD)
2. Composition (or compositions depending on intended cloud providers)
3. Composite Resource Claim (XRC)

Here is a link to Crossplane's [terminology guide](https://crossplane.io/docs/v1.8/concepts/terminology.html)

# How to
I'm going to assume you already have a Kubernetes cluster up and running for the purposes of installing and using Crossplane

1. [Install Crossplane](https://crossplane.io/docs/v1.8/reference/install.html)
2. [Install relevant providers](https://crossplane.io/docs/v1.8/concepts/providers.html#installing-providers)
   * I'm most familiar with AWS so will be focussing my efforts there
3. Install the XRDs and Compositions found within this repo as desired
   * You can `kubectl apply` these
   * I'll look to create proper configuration packages as well down the track (see todo section)
4. Create and apply a Composite Resource Claim to create a Composite Resource which represents an instance of the Composition (a collection of the real world infrastructure)

# Undo

To remove the deployed cloud infrastructure just run through the above steps in reverse with the `delete` function instead of the `apply` function.
Note this will cause Kubernetes to make appropriate delete calls to the relevant cloud provider API and these delete operations are subject to the requirements set by them (i.e. deleting an AWS S3 bucket might fail due to it not being empty first)

# TODO
* Bundle XRDs and Compositions into configuration packages
