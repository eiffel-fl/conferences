The hitchhicker guide to pod security
-------------------------------------

The goal of this session is to show of to enable pod security on k8s clusters.

Pod security is at the moment in beta, but should be release for k8s 1.25.
It is a built-in admission controler which encourages k8s best practices.
You can migrate from pod security policy to pod security.

It comes with 3 policy levels ranging from permissive to restrictive.
The policies are applied in a specific mode per namespace.
There are 3 levels for pod security standards:

1. Privileged.
2. Baseline.
3. Restricted.

The pods modes are the following:

1. Enforce.
2. Audit.
3. Warn.
