Debugging ``go`` programs with eBPF
===================================

State of ``delve``
------------------

Delve turns 9 this year!!!
Since 2020, there were 18 releases, a new ``delve`` release is done each time the new ``golang`` release candidate is marked as OK.
The debugger supports ``golang`` from 1.14 to 1.20, you always have a debugger for whatever ``golang`` version!
Delve has now a DAP server integrated so it eases the editor support, such a using ``delve`` through VScode.
You can also generate a ``core dump`` on running process and they also added support for hardware watchpoints which was a tricky feature to implement.

They recently added an experimental eBPF based tracing backend.
They are currently working on the ability to debug multiple processes simualtaneously!!!

eBPF
----

You use the ``trace`` ``delve`` subcommand which will trace each function which name matches the given argument.
It will print when the function is called and what is its return value.
Using ``--trace-with-stack``, you will also get the stack trace.

Delve uses ``ptrace`` syscall, like a lot of debugger, to trace functions.
Sadly, it is a kinda slow, the overhead can be of several order of magnitude (from microseconds to seconds).
It is indeed slow because it is a syscall, so context switch are costly.
Also, you need to call ``ptrace`` twice: one when entering the function and the other when exiting it.

Compared to ``ptrace``, eBPF is faster because you avoid context switching since they are executed in kernel space.

For a new tracing backend, ``delve`` would need to trace arbitrary functions, to do so they rely on the ``cilium/ebpf`` package.
They first load the eBPF program which is packaged in ``delve`` and attach uprobes for each symbol.
They use eBPF ring buffer to read information from kernel space to user space.

To use ``eBPF`` you need to use ``--ebpf`` for the ``trace`` command.
