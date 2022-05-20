Better Bandwidth Management with eBPF
-------------------------------------

There are more and more pods per nodes because people use more and more k8s.
In k8s, you can set the ingress and egress bandwidths for each pod.
There are design issues with both `kubernetes.io/ingress-bandwith` and `kubernetes.io/egress-bandwith`, among others, there is a single lock contention point across all CPU.

The goal would be to get rid of queue.
People from Google conceptualized the Earliest Departure Time (EDT) idea.
The Cilium bandwith manager permits a lock-less EDT-based pod rate-limiting.
Indeed, the eBPF program has a multi-queue aware packet scheduler which implements EDT.
This solution permits reducing by 4.2 times the latency of the 99th percentile for a ping pong exchange.

Google Research invented BBR which changes the behaviour of TCP to quickly ramp up the bandwith.
Using TCP BBR permits to get an increase of 2 times the average bandwith compared to TCP CUBIC.
Sadly, BBR cannot be used with pods due to timestamp being set to zero.
Indeed, the kernel uses `CLOCK_TAI` for ingress and `CLOCK_MONOTONIC` for egress.

But Linux 5.18 and above will retain timestamps, so it become possible to use BBR with pods.
BBR is more aggressive than CUBIC, so it is better to not mix nodes with BBR and CUBIC.
But Google Research people are working on BBR v2.
Cilium Bandwith Manager supports BBR since v1.12.
