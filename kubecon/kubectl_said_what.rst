Kubectl Said What?
------------------

K8s resources have conditions, phases, states and status.
Decoding all these information can be difficult when learning k8s.

Controllers track conditions realted to pods under their control.
For a `Deployment` or `ReplicatSet`, `ReplicaFailure` happens when one of its pods fails to be created/deleted.

Pod phases are "macro states" which represent the lifecycle of a pod.
If `Pending`, it means the pod was accepted by the system but at least 1 container has *not* been created.
`Unknown` most likely means there is a communication error with `kubelet`.
`Pending` can also be caused by, among others, the following:

* insufficient resources (*e.g.* the pod request 2 CPU but the node has only one),
* missing volumes,
* and selectors (*e.g.* the pod namespce does not exist).

`kubectl describe` gives more fresh information than `kubectl get pod`, particularly if there is a problem with the `kubelet`.
