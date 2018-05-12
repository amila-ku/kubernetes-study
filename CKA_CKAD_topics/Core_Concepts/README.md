# Kubernetes Core Concepts

Kubernetes means helmsman(The one who pilots a ship) which aligns with docker container referances to shipping industry.

## Container Benefits

- Easy to deliver immutable applications



## Kubernetes Components

- Master:
  - [ETCD](https://kubernetes.io/docs/concepts/overview/components/#etcd)
  - [kube-apiserver](https://kubernetes.io/docs/concepts/overview/components/#kube-apiserver)
  - [kube-controller-manager](https://kubernetes.io/docs/concepts/overview/components/#kube-controller-manager)
    - Node Controller
    - Replication Controller
    - Endpoints Controller
    - Service Account & Token Controllers
    - Route Controller
    - Service Controller
    - Volume Controller
  - [kube-scheduler](https://kubernetes.io/docs/concepts/overview/components/#kube-scheduler)
  - [cloud-controller-manager](https://kubernetes.io/docs/concepts/overview/components/#cloud-controller-manager)
- Nodes:
  - [kubelet](https://kubernetes.io/docs/concepts/overview/components/#kubelet)
  - [kube-proxy](https://kubernetes.io/docs/concepts/overview/components/#kube-proxy)
  - Container Runtime (Docker, rkt, runc and any OCI runtime-spec implementation)
- AddOns:
  - [DNS](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/)
  - Dashboard