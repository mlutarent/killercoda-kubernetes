* [Demystifying kube-proxy](https://mayankshah.dev/blog/demystifying-kube-proxy/)
* [K8s: A Closer Look at Kube-Proxy](https://betterprogramming.pub/k8s-a-closer-look-at-kube-proxy-372c4e8b090)

* Jeder POD bekommt eine Cluster-weit eindeutige IP
* Pods können sich gegenseitig über ihre IPs erreichen, egal auf welchem Host/Node sie laufen und ohne NAT
* Services habe eine IP um Set von Pods erreichen zu können
* CNI Plugins setzen diese "Spec" um

* kube-proxy läuft auf jedem Node
* überwacht Services und Endpoints und managed die entsprechenden Regeln per default mittels IPtables im iptables mode

```commandline
ps aux | grep kube-proxy
```

```commandline
kubectl run nginx --image=nginx
kubectl get pods -o wide
```

```commandline
sudo iptables -L -t nat | grep 192.168.1.3
```