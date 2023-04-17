> etcd: A distributed, reliable key-value store for the most critical data of a distributed system [1](https://etcd.io/)

```commandline
ps aux | grep etcd
```

Wir sehen viele Argumente. [Referenz](https://etcd.io/docs/v3.5/op-guide/configuration/)

Der api-server nutzt `--listen-client-urls=https://127.0.0.1:2379,https://172.30.1.2:2379`

Wir nutzen `etcdctl`.

```commandline
etcdctl --cacert=/etc/kubernetes/pki/etcd/ca.crt --key=/etc/kubernetes/pki/etcd/server.key --cert=/etc/kubernetes/pki/etcd/server.crt get / --keys-only --prefix
```
```commandline
# list pods
etcdctl --cacert=/etc/kubernetes/pki/etcd/ca.crt --key=/etc/kubernetes/pki/etcd/server.key --cert=/etc/kubernetes/pki/etcd/server.crt get /registry/pods --keys-only --prefix
```

```commandline
kubectl run nginx image=nginx

etcdctl --cacert=/etc/kubernetes/pki/etcd/ca.crt --key=/etc/kubernetes/pki/etcd/server.key --cert=/etc/kubernetes/pki/etcd/server.crt get /registry/pods/default/nginx
```

```commandline
# delete key from etcd
etcdctl --cacert=/etc/kubernetes/pki/etcd/ca.crt --key=/etc/kubernetes/pki/etcd/server.key --cert=/etc/kubernetes/pki/etcd/server.crt del /registry/pods/default/nginx

kubectl get pods
```

Wenn man ein Backup eines Kubernetes-Clusters erstellen moechte, is eine Backup von etcd fundamental