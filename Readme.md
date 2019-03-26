```
$ minikube start
$ minikube dashboard
$ eval $(minikube docker-env)

$ kubectl proxy
$ docker build -t myapp:v0.0.3 ./project
$ kubectl apply -f ./yaml/nginx-deployment.yaml
```

visit http://localhost:8001/api/v1/namespaces/default/pods/${POD_NAME}:8080/proxy/

- expose service

```
$ kubectl expose deployment/nginx-deployment --type="NodePort" --port=8080
```

- minikube ip => here is your IP
- get the port number
```
$ kubectl get services/nginx-deployment -o go-template='{{(index .spec.ports 0).nodePort}}'
```
- http://${minikube ip}:${PORT}


when finish

```
$ minikube stop
$ minikube delete
```
