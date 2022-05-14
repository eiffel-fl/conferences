Dealing with remote worker nodes
--------------------------------

This talk focus on two projects as consulting:

1. 5G which wants to add edge worker.
2. Hardware which wants to add intelligence to surveillance camera.

In both cases, they do not want to run a full cluster and have, among others, the following needs:

1. High avaibility.
2. Low latency between sites.

5G
==

Based on this, the authors can give best practices for remote worker nodes applied to 5G:

1. Rancher offers multi-cluster management features.
2. The worker node will not have the same processes than the main one (*e.g.* not `etcd` on worker node but a container runtime).

The challenges to do so were the following:

1. Worker nodes need "permanent" contact with the main ones.
2. They may need custom configurations with unreliable links.

One solution to these problem is to use static pods.
The authors may have chose to use HostPath to reduce the worker nodes latency.

The chosen solution is to use Multus with SR-IOV and local VLAN.

Surveillance camera
===================

Each camera is a node which architecture is arm64.

There is a daemon set to be able to select the good pods.
