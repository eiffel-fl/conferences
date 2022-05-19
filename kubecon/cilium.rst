Cilium: Welcome, Vision and Updates
-----------------------------------

Cilium is a lot of thing, among others:
1. A CNI.
2. A service Mesh.
3. Hubble.
4. Tetragon

The CNI supports IPv4 and IPv6 and can handle DNS name based policies.
Hubble provides metrics.

Cilium service mesh offers two options to be used:
1. A sidecar-free with envoy.
2. Istio integration.

Tetragon offers security observability (*e.g.* which syscalls are called).
For example, a process which violates a given rule can be terminated.

Datadog used `iptables` for their load balancing but it was not perfect.
So, they switch to using Cilium.
They also contributed to Cilium and want to continue.

Google k8s service is the first to be based on Cilium.
