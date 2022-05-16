Falco
-----

`sys_enter` acts as a dispatcher toward the corresponding syscall.
For `page_fault_user`, this case does not exist.

One problem of falco is that events can be lost by userspace.
To solve this, the number of events can be reduced by, for example, capture only a given type of events.

To reduce the time taken by the syscall dispatcher when only interested in a given number of syscalls it can be possible to deal with it at the beginning of `sys_enter` before the `bpf_helpers` are called.
