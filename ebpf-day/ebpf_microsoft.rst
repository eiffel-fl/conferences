Getting Linux Based eBPF Programs to Run with eBPF for Windows
--------------------------------------------------------------

The goal of this talk is to show the portability of eBPF production programs from Linux to Windows.

Cilium L4LB uses XDP hook to implement load balancing feature.
96% of the code for load balancing is common within Windows and Linux.

DSR permits the VM which dealt with the request to bypass the load balancing node and directly answered to the client:
* Without: Client <---> load balancing node <---> VM
* With:    Client ----> load balancing node ----> VM
              ^                                    |
              |                                    |
              --------------------------------------


