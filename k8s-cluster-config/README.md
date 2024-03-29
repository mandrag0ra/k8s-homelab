# Configure the cluster with kubectl

Now that the cluster is up and runing, there is still a few steps to walk through to have an environment close to production ready.

Please note: the installation manifests have been uploaded to this repository in order to ensure proper overall operation and to avoid breaking changes due to an update.
You can find the latest installation instructions from the respective websites.

## MetalLB
First, we need to install MetalLB.
MetalLB is a load-balancer implementation for bare metal Kubernetes clusters that uses standard routing protocols such as BGP and L2 1. 

It is a young project, so it should be treated as a beta system. The project aims to provide a network load balancer implementation that integrates with standard network equipment, so that external services on bare-metal clusters also “just work” as much as possible.

In short, it allows you to declare a kubernetes service as loadbalancer.

Version installed : v0.13.12
See latest installation instruction here : https://metallb.universe.tf/installation/

## NFS
This is a simple way to have persistence.
Note than the worker nodes need nfs client to be installed

Version installed : v4.0.2
See latest installation instruction here : https://github.com/kubernetes-sigs/nfs-subdir-external-provisioner/tree/master

## Traefik
Traefik uses Custom Resource Definition to retrieve its routing configuration. Traefik Custom Resource Definitions are a Kubernetes implementation of the Traefik concepts. More informations here : https://doc.traefik.io/traefik/providers/kubernetes-crd/

If Traefik is accessible from the internet, it will be able to automatically generate SSL certificates.
All you need is a valid domain name, with a valid DNS record pointing to your loadbalancer.

Version installed : v2.10
See latest installation instruction here : https://doc.traefik.io/traefik/providers/kubernetes-crd/