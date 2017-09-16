# K8s-Webinar-ConfigMaps-Secrets

## Demo1-ConfigMaps:
Demonstrates use of ConfigMaps for injecting configs via CLI VAR, env VAR and File System

Go to directory:
```
cd  Deploy-Kubernetes/Demo1-ConfigMaps
```

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
This examples shows how to inject Redis config using Configmap. Injection is done thru file system.

Go to directory:
```
cd  Deploy-Kubernetes/Demo2-ConfigMaps
```

Create ConfigMap using Interactive mode:

```
kubectl create configmap example-redis-config --from-file=redis-config
kubectl get cm
```

Create Redis POD:
```
kubectl create -f redis.yml
```

Check:
```
kubectl exec -ti redis sh
 redis-cli
  CONFIG GET maxmemory
  CONFIG GET maxmemory-policy
```


## Demo3-Secrets:

This examples shows how to inject Secrets like username and password to Redis using File System.

Go to directory:
```
cd  Deploy-Kubernetes/Demo3-Secrets
```

Create Secrets:
```
kubectl create secret generic dbsecret --from-file=./username.txt --from-file=./password.txt
```

Create POD using the Secrets inside:
```
kubectl create -f pod-secret.yml
```

Result

```
kubectl exec -ti secret-pod sh
 cd /etc/foo
 more password.txt
 more username.txt
```

 
## Demo4-Secrets

Go to directory:
```
cd  Deploy-Kubernetes/Demo4-Secrets
```

