# Kube 

## How to list all containers name in a pod

```sh
➜  ~ kubectl get pods -n kube-system etcd-kind-control-plane -o jsonpath='{.spec.containers[*].name}'
etcd%
```


