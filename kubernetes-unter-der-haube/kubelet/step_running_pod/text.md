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

<details><summary>controlplane: Folge den Logs des Pods</summary>

```plain
kubectl logs nginx
```

</details>

