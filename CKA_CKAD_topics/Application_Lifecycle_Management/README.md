# Application Design & Lifecycle Management 

## Curriculam: CKA 8%, CKAD-Pod-Design 20%


Pod:
----
Pods are the lowest compute unit of Kubernetes. Pods can contain multiple containers and volumes.Each Container in a pod runs in its own cgroup but they share many Linux namespaces.
- network, UTS, IPC

containers running in same pod share the same ip address.

Replication Set:
-----------------
A ReplicaSet ensures that a specified number of pod replicas are running at any given time. But lacks the capability to manage updates(Rolling Update) for which Deployments should be used.

Deployments:
------------

To ensure that pods are always running, you define a deployment . A deployment is a declarative manifest that describes what Pods should be running and
how many.

Deployment can be edited by kubectl edit or kubectl appy using a manifest. Previous version of replicaset is kept when a new replicaset is created for changed on deployment.



ReplicationController Vs Deployment:
-------------------------------------
ReplicationController also manages a spesified number of replicas are running at a time, but rolling updates done using replication controller is handled through client side and this can cause unxepected states if the connectivity breaks to k8s cluster. Deployment were introduced to prevent this and manage updates from server side.
 
Rolling Updates:
One big advantage of deployments is that they can be used to do a rolling update of your Pods. For
example, let’s assume that you have a new image that you want to use. You can use the kubectl
set command to change that image.

DaemonSet: 
----------

Ensures single pod exists on each cluster node

StatefulSet:
------------

Manages the deployment and scaling of a set of Pods, and provides guarantees about the ordering and uniqueness of these Pods. Similar to Deployments manages pod state according to the spec but unlike deployments StatefulSets maintain stickey identity for pods.


Service : 
---------
A Kubernetes Service is an abstraction which defines a logical set of Pods and a policy by which to access them - sometimes called a micro-service. The set of Pods targeted by a Service is (usually) determined by a Label Selector

Service Types:
Type values and their behaviors are:

ClusterIP: Exposes the service on a cluster-internal IP. Choosing this value makes the service only reachable from within the cluster. This is the default ServiceType.
NodePort: Exposes the service on each Node’s IP at a static port (the NodePort). A ClusterIP service, to which the NodePort service will route, is automatically created. You’ll be able to contact the NodePort service, from outside the cluster, by requesting <NodeIP>:<NodePort>.
LoadBalancer: Exposes the service externally using a cloud provider’s load balancer. NodePort and ClusterIP services, to which the external load balancer will route, are automatically created.
ExternalName: Maps the service to the contents of the externalName field (e.g. foo.bar.example.com), by returning a CNAME record with its value. No proxying of any kind is set up. This requires version 1.7 or higher of kube-dns


Job:
----

Job is intended to run pods that are intended to run and terminate on their own (batch jobs).

[CronJob](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/):
--------

Runs a workload periodically on a given schedule.

