# CoreDNS

> CoreDNS is different from other DNS servers, such as (all excellent) BIND, Knot, PowerDNS and Unbound (technically a resolver, but still worth a mention), because it is very flexible, and almost all functionality is outsourced into plugins.
> Plugins can be stand-alone or work together to perform a “DNS function”.
[What is CoreDNS?](https://coredns.io/manual/toc/)


> This plugin implements the Kubernetes DNS-Based Service Discovery Specification.
> CoreDNS running the kubernetes plugin can be used as a replacement for kube-dns in a kubernetes cluster.
[CoreDNS Kubernetes Plugin](https://coredns.io/plugins/kubernetes/)


# DNS in K8S

[DNS for Services and Pods](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/)

Containers started by Kubernetes automatically include this DNS server in their DNS searches.

DNS ist ein K8s Add-on und als solches nicht *zwingend* fuer den Betrieb von K8S noetig, wird aber dringen empfohlen

```commandline
ps aux | grep coredns
```

What objects get DNS records?
    Services
    Pods

```commandline
kubectl get svc -A

# Wir sehen den entsprechenden Service
kube-system   kube-dns     ClusterIP   10.96.0.10   <none>        53/UDP,53/TCP,9153/TCP   8d
```

```commandline
kubectl describe cm coredns -n kube-system

Corefile:
----
.:53 {
    errors
    health {
       lameduck 5s
    }
    ready
    kubernetes cluster.local in-addr.arpa ip6.arpa {
       pods insecure
       fallthrough in-addr.arpa ip6.arpa
       ttl 30
    }
    prometheus :9153
    forward . /etc/resolv.conf {
       max_concurrent 1000
    }
    cache 30
    loop
    reload
    loadbalance
}
```
```commandline
kubectl create ns dns1
kubectl run pod1 --image=nginx -n dns1
kubectl run pod2 --image=nginx -n dns1

kubectl exec -n dns1 pod1 -- cat /etc/resolv.conf

# pod2 kann pod1 nicht per DNS erreichen, weil der Service fehlt
kubectl exec -n dns1 pod2 -- curl pod1
kubectl expose pod/pod1 -n dns1 --port=80
kubectl exec -n dns1 pod2 -- curl pod1

# das würde allerdings auch ohne Service gehen
kubectl exec -n dns1 pod2 -- curl <ip of pod>.dns1.pod.cluster.local
```