# Use Port Forwarding to Access Applications in a Cluster


主要是讲对于一个启用了ClusterIP的service，我们可以用kubectl port-forward把端口开放给本机

https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/


```bash
kubectl apply -f mongo-deployment.yaml

# Deploy mongo service
# ClusterIP mode
kubectl apply -f mongo-service.yaml

# kubectl forward a clusterIP service 
# 把service暴露的ClusterIP:27017 
kubectl port-forward service/mongo 28015:27017
```


```bash
# Additional 
# Have a machine connection to mongo using clusterIP
# spawn a new mongo client deployment
kubect apply -f mongo-client-deployment.yaml
kubect exec -it MONGO-CLIENT-POD-NAME -- bash
```