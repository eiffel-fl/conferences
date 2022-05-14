Buildscaler
-----------

CI/CD are often PaaS but it is hard to install it yourself and to host it.
Nowadays, it is easier, for example Gitlab and GitHub released their runners so you can install them.

You may want to host your own CI/CD for the following reasons:

1. Security.
2. Cost.
3. Speed (by having your CI/CD near your dependencies).

To orchestrate your CI/CD, you may want to use k8s.
Then, you may want to scale the pods and particularly to scale with CI related metrics.
If you use prometheus metrics, you may want to translate to them to k8s ones.

Buildscaler addresses the problem of metrics translation.
By removing some components, you actually improve the reactivity of the system.
