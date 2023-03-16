<details><summary>node01: Stoppe Kubelet</summary>

```plain
systemctl stop kubelet
```

</details>

<details><summary>controlplane: Läuft der Pod noch</summary>

```plain
kubectl get pod -o wide
```

</details>

<details><summary>controlplane: Sind die logs noch da?</summary>

```plain
kubectl logs nginx
```

</details>
