# Run a Replicated Stateful Application

https://kubernetes.io/docs/tasks/run-application/run-replicated-stateful-application/

## Deploy MYSQL

This ConfigMap provides my.cnf overrides that let you independently control configuration on the primary MySQL server and replicas. In this case, you want the primary server to be able to serve replication logs to replicas and you want replicas to reject any writes that don't come via replication.

There's nothing special about the ConfigMap itself that causes different portions to apply to different Pods. Each Pod decides which portion to look at as it's initializing, based on information provided by the StatefulSet controller. Pod在启动时可以通过stateful deployment提供的信息得知其是主MySQL还是从MySQL

```
# ConfigMap
kubectl apply -f mysql-confmap.yaml
# Service 注意 headless service的作用是提供一个dns解析，让cluster内部的app可以用过<PODNAME>.mysql 这样的一个域名直接访问到service
kubectl apply -f mysql-services.yaml

# 
```

