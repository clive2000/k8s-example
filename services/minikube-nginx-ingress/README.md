# Using nginx ingress controller in minikube

```
minikube addons enable ingress

kubectl apply -f app.yaml
kubectl apply -f service.yaml

kubectl apply -f example-ingress.yaml

kubectl get ingress # Copy the ADDRESS
# Go to local machine's /etc/hosts
# Create a mapping between ADDRESS and domain hello-world.info
```

## Deploy second app

```
kubectl create deployment web2 --image=gcr.io/google-samples/hello-app:2.0

kubectl expose deployment web2 --port=8080 --type=NodePort
```

Add following to example-ingress.yaml
```
      - path: /v2
        pathType: Prefix
        backend:
          service:
            name: web2
            port:
              number: 8080
```

Finally run `kubectl apply -f example-ingress.yaml` again

And then `curl hello-world.info/v2`