```commandline
ps aux | grep kube-scheduler
```

```commandline
cat /etc/kubernetes/scheduler.conf
```

Der scheduler hat seine eigene config, um mit dem API-server kommunizieren zu koennen, mit dem user `system:kube-scheduler`.

```commandline
kubectl describe pod test1
```

Wir sehen `Normal  Scheduled  10m   default-scheduler  Successfully assigned default/test1 to node01`.

