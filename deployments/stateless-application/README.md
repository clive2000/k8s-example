# Run a stateless application using deployment

```bash
# Deploy nginx app
kubectl apply -f nginx-deployment.yaml

# If at a later time, you need to udpate your nginx
kubectl apply -f nginx-update.yaml

# Scale replica to 4
kubectl apply -f nginx-scale-to-4.yaml
```