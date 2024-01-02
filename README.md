# K8s Homelab

Yet another repository to install and configure Kubernetes on bare metal from scratch.

QEMU vms installed on Proxmox were used in this example. That said, the ansible playbooks can be used on any platform, as long as the prerequisites are met.

Requirements :
- At least 2 Debian 12 servers, 1 master and 1 slave. Recommanded : 1 master and 3 slaves
  - every servers have to be able to speak with each other
  - if you want to use NFS for persistence, the server will need to be installed and configured. The deployment manisfest on kubernetes is provided 
- A local user with sudo privileges who wil execute kubectl commmand has to exist

In the first part, you will find the ansible playbooks which will allow you to prepare the cluster.

Once the Kubernetes cluster is up and running, you will find the manifests that will allow you to configure MetalLB, to allow loadbalancing, the use of an NFS server as well as Traefik as Ingress Controller. Traefik also allows the automatic generation of SSL certificates.
