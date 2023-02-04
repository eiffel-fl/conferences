U-Boot as PSCI provider on ARM64
================================

Power State Coordination Interface (PSCI) is mandatory on ARMv8a.
It exists due to convenience rather than copy/pasting code for several CPU.
It removes the complexity and avoid the kernel do damage the hardware.
You can store this in the firmware which is updated by the bootloader but this can be tricky.
It also eases CPU core state management in virtualization.

It relies on SMC Call Convention.
It defines a convention between SMC (Supervisor) and HVC (Hypervisor) instructions.
To execute a given function, you store its ID in ``x0`` register then the parameters in ``x1`` to ``x6``, and you call either ``smc`` or ``hvc``.
The result is stored in ``x0``.
The functions are defined in ``arch/arm/include/asm/pci.h`` in U-Boot source code.

U-Boot and the Linux kernel call this function and the handlers are in U-Boot and ATF source code.
The handlers are in assembly and the caller call inline assembly.
It exists a ``smc`` ``hush`` command in U-Boot!
If Linux is virtualized, it calls the ``hvc``, otherwise the ``svc``.

When U-Boot runs on UP, it runs in EL3 (Hypervisor) so sadly the calls will not work because they use ``smc``.
