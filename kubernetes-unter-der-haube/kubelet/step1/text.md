Wir verschaffen uns zunächst einen Überblick:

*Welche Nodes laufen im Cluster?*

<br>

<details><summary>Solution</summary>

```plain
kubectl get nodes
```

</details>

<br>

*Welche Pods laufen auf welchen Nodes?*

<br>

<details><summary>Solution</summary>

```plain
kubectl get pods -o wide -A
```

</details>
