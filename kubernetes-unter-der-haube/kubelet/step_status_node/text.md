Wir haben mittels *kubectl* gesehen, dass auf dem Worker-Node Pods laufen.
Wo genau laufen sie denn?

<details><summary>Laufen docker container?</summary>

```plain
docker ps
```

</details>

<details><summary>Laufen irgendwelche CRI-Container?</summary>

```plain
crictl ps
```

*CRI = Container Runtime Interface*

</details>

Wir haben bereits gehört, dass *kubelet* ein Service bzw. ein Agent ist, der auf dem Worker-Node läuft.

<details><summary>Wo genau läuft der kubelet Prozess?</summary>

```plain
ps aux | grep kubelet
```

```plain
systemctl status kubelet
```

</details>
