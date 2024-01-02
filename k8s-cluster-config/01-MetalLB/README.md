# MetalLB

In a Kubernetes cluster on a cloud provider, you request a load balancer, and your cloud platform assigns an IP address to you. 
In a bare-metal cluster, as with Proxmox, MetalLB is responsible for that allocation.

## Installation
This cluster has been initialise with metalLB v0.13.12.

## Configuration
Declare the IPAddressPool Custom ressource :
In layer2-configuration.yml file, adapt `addresses` based on your configuration (10.0.0.100/32 in our example).
It has to be in the same subnet has your nodes and not being used.

Then, apply this manifest :
```
kubectl apply -f metallb-native.yaml
```

```
kubectl apply -f layer2-configuration.yml
```
## Is it working properly
The output of these 2 commands can confirm that metallb works correctly :
```
kubectl get pods -n metallb-system
kubectl describe configmap -n metallb-system
```