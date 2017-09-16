# K8s-Webinar-ConfigMaps-Secrets

## Demo1-ConfigMaps:
Demonstrates use of ConfigMaps for injecting configs via CLI VAR, env VAR and File System

Deploy ConfigMaps:
```
kubectl create -f configmap.yml
```

Deploy POD pod-cmd (injection via CLI VAR):
```
kubectl create -f pod-cmd.yml
```

Check:
```
kubectl logs test-pod-cmd
```


Deploy POD pod-env (injection via ENV VAR):
```
kubectl create -f pod-env.yml
```

Check:
```
kubectl exec -ti test-pod-env sh
env
```

Deploy POD pod-vol (injection via File System):
```
kubectl create -f pod-vol.yml
```

Check:
```
kubectl exec -ti test-pod-vol sh
cd /etc/config
more log.level
more log.location 
```


## Demo2-ConfigMaps:


## Demo3-Secrets:


## Demo4-Secrets
