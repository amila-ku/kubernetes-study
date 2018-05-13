# kubernetes-study
Material for Studying Kubernetes and Preparing for Kubernetes certificatios

[Concepts Overview](https://kubernetes.io/docs/user-journeys/users/application-developer/foundational/#section-2)

# Kubectl Examples

## pods

Create Pods:
``` 
kubectl run --generator=run-pod/v1 fooweb --image=nginx
kubectl run --restart=Never fooweb --image=nginx

```

[more about generator](https://kubernetes.io/docs/reference/kubectl/conventions/#generators)

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

Create Pods with requests, limits and service account:
``` 
kubectl run --generator=run-pod/v1 foobar --image=nginx — serviceaccount=foobar --requests=cpu=100m,memory=256Mi --limits=cpu=100m,memory=256Mi

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

use with --record to record changes

```
kubectl run fooweb --image=nginx --port=80 --record

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

Scale a Deployment
```
kubectl scale nginx --replicas=5

```


AutoScale a Deployment when [Horizontal Pod Autoscaling enabled] (https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)
```
kubectl autoscale deployment nginx-deployment --min=10 --max=15 --cpu-percent=80

```


Create Service for Deployment
```
kubectl expose deployment nginx --port=443 --target-port=8443 --name=nginx-https

```

Update a Deployment
```
kubectl set image deployment/fooweb nginx=nginx:1.91

```



## Start a Cron Job

Create Replicated Deployment
```
kubectl run pi --schedule="0/5 * * * ?" --image=perl --restart=OnFailure -- perl -Mbignum=bpi -wle 'print bpi(2000)'

```

## Start a Job

Create Replicated Deployment
```
kubectl run pi --image=perl --restart=OnFailure -- perl -Mbignum=bpi -wle 'print bpi(2000)'

```


## Expose Service, Pod

Create Service for Deployment
```
kubectl expose deployment nginx --port=443 --target-port=8443 --name=nginx-https

```

Create Service for Pod
```
kubectl expose pod fooweb --port=8080 --name=frontend

```

Create Service for ReplicationController with Protocol
```
kubectl expose rc streamer --port=4100 --protocol=udp --name=video-stream

```
