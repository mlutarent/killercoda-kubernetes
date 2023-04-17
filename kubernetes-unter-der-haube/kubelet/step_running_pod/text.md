<details><summary>node01: Folge den kubelet logs</summary>

```plain
journalctl -u kubelet -f
```

</details>

<details><summary>controlplane: Starte einen neuen Pod</summary>

```plain
kubectl run nginx --image=nginx
```

</details>

<details><summary>controlplane: Verifiziere den neuen Pod</summary>

```plain
kubectl get pod -o wide
```

</details>

```commandline
kubectl describe pod nginx
```

Wir sehen

```commandline
  Normal  Pulling    10m   kubelet            Pulling image "nginx"
  Normal  Pulled     10m   kubelet            Successfully pulled image "nginx" in 3.338331995s (3.338335271s including waiting)
  Normal  Created    10m   kubelet            Created container nginx
  Normal  Started    10m   kubelet            Started container nginx
```

<details><summary>controlplane: Folge den Logs des Pods</summary>

```plain
kubectl logs nginx
```

</details>

