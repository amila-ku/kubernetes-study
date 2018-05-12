# kubernetes-study
Material for Studying Kubernetes and Preparing for Kubernetes certificatios

[Concepts Overview] (https://kubernetes.io/docs/user-journeys/users/application-developer/foundational/#section-2)

# Kubectl Examples

## pods

Create Pods:
``` 
kubectl run --generator=run-pod/v1 fooweb --image=nginx
kubectl run --restart=Never fooweb --image=nginx

```

Create Pods and Expose Port:
``` 
kubectl run --generator=run-pod/v1 fooweb --image=nginx --port=80
kubectl run --restart=Never fooweb --image=nginx --port=80

```

Create Pods, Expose Port and set Environment Variable:
``` 
kubectl run --generator=run-pod/v1 fooweb --image=nginx --port=80 --env="APPTYPE=foo"
kubectl run --restart=Never fooweb --image=nginx --port=80 --env="APPTYPE=foo"

```

## Replication Controller

Creating Replication Controller:
``` 
kubectl run --generator=run/v1 fooweb --image=nginx

```

## Deployment

Create Deployment:
``` 
kubectl run  fooweb --image=nginx
kubectl run --generator=apps/v1beta fooweb --image=nginx

```

Create Deployment, Expose Port and set Environment Variable:
``` 
kubectl run  fooweb --image=nginx --port=80 --env=APPTYPE=foo
kubectl run --generator=apps/v1beta fooweb --image=nginx --port=80 --env="APPTYPE=foo"
kubectl run hazelcast --image=hazelcast --env="DNS_DOMAIN=cluster" --env="POD_NAMESPACE=default"

```

Create Deployment and set Labels:
``` 
kubectl run fooweb --image=nginx --labels="app=hazelcast,env=prod" --port=80 --env="APPTYPE=foo"

```

Create Replicated Deployment
```
kubectl run nginx --image=nginx --replicas=5

```