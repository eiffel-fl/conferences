meta netdevices
===============

The goal is to leverage BPF architecture to achieve maximum performance for kubernetes pods networking.

In 2021, the median number of containers per host was 46, and there 33% of nodes which would count between 16 and 25 pods.
You can do the routing via BPF to short circuit the upper stack.
With this, the lateny decreases from 101 µs/MB to 92 µs/MB, which is around a 10% improvement.

So, instead of using ``veth`` device, they developped ``meta`` netdevices.
With this, you avoid having a soft IRQ, hence avoid a schedule operation.
A ``meta``driver is around 500 lines of code.
By using these devices, you mproves the latency from 92 to 85 µs/MB, which is near the baseline of the host latency.

By combining this with BIG TCP, you get the host latency which is perfect.
The ``copy_to_user()`` are costly in CPU cycles, a solution to avoid this would be to use TCP zero-copy but it would need applications to be adapted.
