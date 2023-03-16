## Was läuft bereits?

Welche Nodes laufen im Cluster?


Welche Pods laufen auf welchen Nodes?


### Solution

```plain
kubectl get nodes
kubectl get pods -o wide -A
```{{exec}}
