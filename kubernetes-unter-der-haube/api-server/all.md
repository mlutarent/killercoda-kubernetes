

```commandline
ps aux | grep kube-apiserver
```

Der kube-apiserver-Prozess läuft auf dem control-plane
Interessant sind die relativ vielen Argumente. [Siehe API server Referenz](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/)


```commandline
crictl ps
```

Letztlich laueft der api-server als Container

```commandline
curl https://127.0.0.1:6443 -k
```

Wir koennen einen Request and den api-server schicken. Wir sind nicht authorisiert.

```commandline
kubectl get pods -v8
```

Wir sehen, dass ein Request auf `https://172.30.1.2:6443/api/v1/namespaces/default/pods?limit=500` gemacht wurde.
`loaded from file:  /root/.kube/config` verraet uns, wo die Credentials liegen.

```commandline
kubectl run test1 --image=nginx -v8
```

Wir sehen etwas wie `POST https://172.30.1.2:6443/api/v1/namespaces/default/pods?fieldManager=kubectl-run 201 Created in 12 milliseconds`.

```commandline
kubectl get po
```

Unser pod laeuft.
