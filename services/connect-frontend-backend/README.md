# Connect frontend to backend

可以用服务把frontend component和backend component连接起来

```bash
# Deploy backend first
kubectl apply -f backend-app.yaml
kubectl apply -f backend-service.yaml

# Deploy frontend 
kubectl apply -f frontend-service.yaml
kubectl apply -f frontend-app.yaml
```

这里头实际上发生的是backend-service注册了一个service名称hello.然后front-end是一个nginx image，其中的配置文件如下，可以通过这个配置文件，把把请求全部proxy到后端的hello上。从而实现了front-end和backend的通信


```nginx
# The identifier Backend is internal to nginx, and used to name this specific upstream
upstream Backend {
    # hello is the internal DNS name used by the backend Service inside Kubernetes
    server hello;
}

server {
    listen 80;

    location / {
        # The following statement will proxy traffic to the upstream named Backend
        proxy_pass http://Backend;
    }
}

```