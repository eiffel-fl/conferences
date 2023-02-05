Hardening Kernel Subsystems by Architectural Capabilities
=========================================================

Hardening OS correctly is complicated because they are complex.
It exists various security features, like LSM, eBPF or ``seccomp``.
A lot of hardware security features are also added to CPU, like TEE on ``arm``.
For a given SoC, you will have several.

The concept of a capability-based security model is to add dedicated instructions and fine-grained memory protection (for MIPS, RISC and ARM ``v8a``).
`Morello git.morello-project.org`_ extends the Arm v8.2-A with a capability-based security model.
It adds 129 bits pointers which adds metadata like the permissions on a pointer.
With this, you can say if this pointer can be loaded, stored or executed.

In the Linux kernel, there are several maintainers for Morello ABI.
It contains a pure capability ABI and also many kernel features are added.
All pointers passed to or provided by the kernel to syscalls use the above capabilities.
For example, to use TEE, it was needed to change the type of TEE ``ioctl`` pointers to use the capabilities pointers rather than conventionnal ``unsiged long``.

As future work, they plan to combine software defined permission with hardware defined ones, *e.g.*, to have better syscall sandboxing.
