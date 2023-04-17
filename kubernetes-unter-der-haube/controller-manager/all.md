
[Controllers](https://kubernetes.io/docs/concepts/architecture/controller/)

> In Kubernetes, controllers are control loops that watch the state of your cluster, then make or request changes where needed. 
> Each controller tries to move the current cluster state closer to the desired state.

> A controller tracks at least one Kubernetes resource type. These objects have a spec field that represents the desired state. The controller(s) for that resource are responsible for making the current state come closer to that desired state.

> The controller might carry the action out itself; more commonly, in Kubernetes, a controller will send messages to the API server that have useful side effects.

> Kubernetes comes with a set of built-in controllers that run inside the kube-controller-manager. These built-in controllers provide important core behaviors.

> Examples of controllers that ship with Kubernetes today are the replication controller, endpoints controller, namespace controller, and serviceaccounts controller

```commandline
ps aux | grep kube-controller-manager
```

Man beachte `--authentication-kubeconfig=/etc/kubernetes/controller-manager.conf`

Wir stellen den controller manager ab:

```commandline
mv /etc/kubernetes/manifests/kube-controller-manager.yaml /tmp/
ps aux | grep kube-controller-manager
```

Wir koennen trotzdem einfache Pods starten:

```commandline
kubectl run test2 --image=nginx
```

Bei deployments hakt aber etwas:

```commandline
kubectl create deployment deploy1 --image=nginx
```

```commandline
kubectl describe deployments.apps deploy1
```

Wir stellen den controller manager wieder an:

```commandline
mv /tmp/kube-controller-manager.yaml /etc/kubernetes/manifests/
```

Und nach kurzer Zeit laeuft der Pod.