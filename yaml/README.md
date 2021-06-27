# yaml

deploy yaml of k8s

## create

```
kubectl create -f sa.yaml
kubectl create -f role.yaml
kubectl create -f role-binding.yaml
kubectl create -f server.yaml
kubectl create -f client.yaml
```

## check

```
kubectl logs -f client
```

## delete

```
kubectl delete -f sa.yaml
kubectl delete -f role.yaml
kubectl delete -f role-binding.yaml
kubectl delete -f server.yaml
kubectl delete -f client.yaml
```