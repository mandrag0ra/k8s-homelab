# Cluster configuration with ansible

Ansible plybook to install and configure servers to host the kubernetes cluster

## Requirements
- At least 2 Debian 12 servers, 1 master and 1 slave. Recommanded : 1 master and 3 slaves
  - every servers have to be able to speak with each other
  - if you want to use NFS for persistence, the server will need to be installed and configured. Deployment on kubernetes is provided 
- A local user with sudo privileges who wil execute kubectl commmand has to exist. His username has to be set in `group_vars/all.yml`.

## Kubernetes version
The playbooks were tested with version v1.28 of Kubernetes.
This can be changed in `group_vars/all.yml`.

## Haproxy
Install haproxy to facilitate redirection of traffic to the K8s cluster.
In this example, it will send all requests to the Kubernetes Traefik Ingress Controller.
