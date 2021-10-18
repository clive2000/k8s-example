# Use LoadBalancer with minikube-loadbalancer

https://minikube.sigs.k8s.io/docs/handbook/accessing/#loadbalancer-access

```
kubectl apply -f app.yaml

# Create service
kubectl apply -f loadbalancer-service.yaml
```