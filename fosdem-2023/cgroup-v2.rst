7 years of cgroup v2: the future of Linux resource control
==========================================================

Cgroup is mechanism to isolate and balance resources between containers.
The difference between cgroup v1 and v2 is that there is no more hiearchy.

When there is memory pressure, it leads to memory reclaim which leads to disk I/O and poor performance.
Also, the memory reclaim is a CPU-cycles heavy process.
We need to make more efficient of the existing resources than paying new ones.

Chrome is binary is more than 1MB, which is really big!
At Meta, there is a daemon which collects statistics across machines and which is a bit memory hungry.

``memory.current`` in `cgroup v2``gives the truth but sometimes it is complicated (anonymous *vs* file).
You need to find the working set of application, sometimes you can reduce a bit the memory and nothing happens for your performance.
But if you reclaim the working set, you are dead.
```senpai`` bit.ly/cgsenpai`_ is a tool you can use to monitor memory pressure and computing it by decreasing the ``memory.high``.

There is a figure of the memory pyramid, as the top they are fast, small but expensive (*w.r.t.* to price per GB).
At the bottom, they are slow, big and not so much expensive.
``zswap`` is a compressed RAM cache.

In kernel 5.8, the swaping algorithm was modified.
If a file page is repeatedly faulting/evicting, then a heap page is evicted instead.
There is a trade between pages, so no I/O are added.
It increases the performance, for web server, decreases the heap memory and also increases the page cache memory.
The performance can be seen `here bit.ly/tmopost`_.

It is really hard to set a "good" limit to disk bandwith due to the complexity of mount volumes.
So, it is better to give latency instead.
But it works well for one unique workload.
So, the idea is to use `QoS bit.ly/iocost`_.
