Hybrid Networking Stack Demo
============================

An Hybrid Networking Stack is a stack which relies on XDP or AF_XDP without reimplementing the full Linux network stack.
There is a control plane and user plane separation.
The traffic is filtered as early as possible in your stack, for example at hardware level if your hardware permits it, otherwise at XDP level.

Cloud Native Data Plane (CNDP) is an open source framework, it comes with:

1. A set of userpace libraries to speed up packet processing for cloud applications.
2. A Hybrid Networking Stack.
3. Kubernetes components to provision and manage a CNDP deployment.

The performance with AF_XDP depends on the scenario.
