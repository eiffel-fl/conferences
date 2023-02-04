Barebox, the bootloader for Linux kernel developers
===================================================

Barebox was at the basic thought as U-Boot v2.
It has monthly releases, around 330 contributors and there is a layer for Yocto (``meta-ptx/meta-barebox``)
In terms of contribution, it adds around 14OO commits per year.

Regarding design, it does the following:

1. Use a stripped down Linux device/driver model.
2. Runtime configuration is done via device tree and/or ``Kconfig`` options.
3. Ruse stripped down drivers.

Add a new driver
----------------

You need to follow these instructions:

1. Copy/paste the code from Linux.
2. Change includes from Linux to barebox ones.
3. Remove Linux kernel specific function. Mainly replacing IRQ by polling because barebox does not support IRQ.
4. Add the ``Kconfig`` and ``Makefile`` corresponding entries.

It feels like writing a kernel driver!

Nonetheless, porting a framework driver, like GPIO, takes more effort.

Image layout
------------

The image layout is mainly composed of:

1. SoC header.
2. Pre-BootLoader (PBL).
3. Device tree blob
4. Other firmware.
5. The bootloader itself.

Add a new board
---------------

You will need to write a PBL, which does not have any support for device tree.
Its main goal is to setup few systems (like UART or ATF which setups DDR) and then starts ``barebox``.

For the bootloader itself, you need to take into account board specific boot decisions, then apply board specific fixups (*e.g.* device tree overlays).
You can try running barebox `online https://barebox.org/jsbarebox`_.
You can also update the bootloader with the ``barebox_update`` command.
