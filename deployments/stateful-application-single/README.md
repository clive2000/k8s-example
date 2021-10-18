# Deploy a single-instance stateful application

https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/

## Create service

```bash
# Create pv and pvc first
kubectl apply -f mysql-pv.yaml

# Create deployments and service
kubectl apply -f app.yaml

# Run a one-off image to connect to mysql
kubectl run -it --rm --image=mysql:5.6 --restart=Never mysql-client -- mysql -h mysql -ppassword
```

## Delete deployments

```
kubectl delete deployment,svc mysql
kubectl delete pvc mysql-pv-claim
kubectl delete pv mysql-pv-volume
```