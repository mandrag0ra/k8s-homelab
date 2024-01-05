# Traefik

Traefik is a reverse proxy and load balancer that is designed to work with Kubernetes. It is used to route incoming traffic to the appropriate service within the cluster.
Traefik can also be used to manage SSL certificates for services running in the cluster.
Traefik engineering team developed a Custom Resource Definition (CRD) for an IngressRoute type, defined below, in order to provide a better way to configure access to a Kubernetes cluster.

This will install the latest known traefik version v2.10 as of December 2023

## IngressRoute Definition
### Install Traefik Resource Definitions:
```
kubectl apply -f deploy/crd-definition-v1.yml
```

### Install RBAC for Traefik:
```
kubectl apply -f deploy/crd-rbac.yml
```

## Volumes
### If you want to create Persistent Volume
```
kubectl apply -f deploy/persistent-volume-claim.yml
```

## Service
```
kubectl apply -f deploy/service.yml
```

## Deployments
```
kubectl apply -f deploy/deployment.yml
```

## Your app example
Modify `<DOMAIN_NAME>` in `test/test-app.yml` with your host, using a fully working DNS record.

### Deployment
```
kubectl apply -f test/test-app.yml
```
