## Kubelet - Der primäre "node agent"

![Die klassischen Kubernetes Komponenten](https://d33wubrfki0l68.cloudfront.net/2475489eaf20163ec0f54ddc1d92aa8d4c87c96b/e7c81/images/docs/components-of-kubernetes.svg)

In diesem Szenario schauen wir uns *Kubelet* genauer an.

*Kubelet* ist ein Service bzw. Agent, der auf jedem Worker-Node läuft.
Seine Hauptaufgabe ist es, Container (Pods) zu starten und zu beenden.
