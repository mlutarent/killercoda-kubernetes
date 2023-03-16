Wir verschaffen uns zunächst einen Überblick:

* Welche Nodes laufen im Cluster?
* Welche Pods laufen auf welchen Nodes?

<br>

```plain
kubectl get nodes
kubectl get pods -o wide -A
```{{exec}}
