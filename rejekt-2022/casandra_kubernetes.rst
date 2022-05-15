Bringing Apache Cassandra closer to Kubernetes
----------------------------------------------

Casandra architecture assumes the following:

1. It runs on fixed hardware.
2. All nodes perform all actions.
3. It scales all resources (data, compute and network) or nothing at all.
4. It does not autoscale.

The goal is to make Cassandra more serverless, by, among others:

1. Make it scales accross different axes (*e.g.* data size, cpu *vs* storage, *etc.*).
2. Make it scales quickly and cheaply.
3. Make it running on k8s.

To do so, Cassandra was split into several serverless services.
