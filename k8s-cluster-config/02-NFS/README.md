# NFS subdir external provisioner

In Kubernetes, NFS can be used to provide persistent storage for applications running in the cluster.

NFS subdir external provisioner is an automatic provisioner that uses your existing and already configured NFS server to support dynamic provisioning of Kubernetes Persistent Volumes via Persistent Volume Claims.

You can find more details on [the github project](https://github.com/kubernetes-sigs/nfs-subdir-external-provisioner)

## Requirements

NFS server installation is not covered here. But there are several simple examples on the Internet.
The NFS server has to be reachable from each node of the kubernetes cluster.

## Deploy
The deploy folder was cloned from the project's github repository, as recommanded. It's the latest version as of December 1, 2023.

### Service Account
Create the Service Account :
```
kubectl apply -f deploy/rbac.yaml
```

### Create a new storage class
```
kubectl apply -f deploy/class.yaml
```

### Create the deployment for “nfs-subdir-external-provisioner”
Edit `deploy/deployment.yaml` to suit to your needs. Ajust `<YOUR_NFS_SERVER_HOSTNAME>` and `<YOUR_NFS_PATH>`.
Then deploy with :
```
kubectl apply -f deploy/deployment.yaml
```

### Test
Now we can test our NFS server :
```
kubectl create -f test/test-claim.yaml -f test/test-pod.yaml
kubectl get all -A
```
