What have we learned from scanning over 10K unique clusters with Kubescape?
---------------------------------------------------------------------------

K8s is here to stay and so is targeted by attackers and sadly current security solution fails to provide "devops" experience.
Most of the security incidens are due to misconfiguration mistakes.

Kubescape is an open source tool which analyzes the risk and compliance, offers an RBAC visualizer and also an image scanner.
A third of the 10K scanned clusters were in the USA and 57% of the kubescape users were devops.
66% of the scanned clusters had below 10 nodes.

Here are some statistics regarding the scanned clusters:
1. 100% have misconfiguration.
2. 65% have at least one high severity misconfiguration.
3. 37% contain secrets in the configuration.
4. 23% run with dangerous capabilities (*e.g.* `CAP_SYS_ADMIN`).

For example, running a container as priviliged and having user ID below 1000 are considered the most bad practices "in the world".

When using `kubescape`, the printed score (lower is better) should be better than 30.
