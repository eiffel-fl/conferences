Bpftrace Meets Pixie: Dynamic Monitoring of K8s Clusters Unleashed
------------------------------------------------------------------

This talk focuses on pixie and bpftrace.
`bpftrace` allows you use create tracepoint, for example to trace all `open()` syscalls.

Pixie is a platform for real time k8s debugging.
Using python nand pandas, you can get some particular metrics.
There is a Pixie Edge Module (PEM) for each node, each PEM contains a Stirling which is an eBF collectors.

The idea would be to run `bpftrace` scripts on Pixie to be able to use its easy k8s deployment.
So, the author changed `bpftrace` to make it enable to store events in a DB instead of printing them.
Then, the user can query the DB.

The DB contains table which the number of columns equals the number of printed events.
It is possible to write PxL script which contains the `bpftrace` script to be run, the information on the table.

It is basically inspekor-gadget plus headlamp.
