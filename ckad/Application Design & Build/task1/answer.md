# task 1

```bash
>k run app-env --image=nginx:1.25 --labels=APP_MODE=production,APP_VERSION=1.0
pod/app-env created

>k get pods
NAME      READY   STATUS              RESTARTS   AGE
app-env   0/1     ContainerCreating   0          3s

> k get pods
NAME      READY   STATUS    RESTARTS   AGE
app-env   1/1     Running   0          9s
```
