Overview and State of Linkerd
-----------------------------

Linkerd is a different kind of service mesh.
A service mesh gives you:

1. Observability: you can get metrics like latencies or throughput.
2. Reliability.
3. Security.

Linkerd follows "less is more".
For its data plane, `linkerd` relies on rust.
Istio can be compared to Linkerd but it comes with a lot of features at the cost of complexity.
Linkerd offers the bare minimum but is then easier to understand.

In version 2.9, they added support for mTLS for all protocol and arm64 architecture port.
Since version 2.10, almost everything was made modularized, so optional.
