openSUSE MicroOS design
=======================

It still uses RPM packages and they offer the same than in Tumbleweed, as well as ``btrfs`` to use snapshot and Copy-on-Write.
Compared to Tumbleweed, it has a read-only root file system, which is pretty common to container image based.
It is a single purpose system, so you will need to use containers to run your application.

They take ``btrfs`` on the root filesystem, so not on your containers are they are run inside the ``/var`` directory.
If the snapshot was successful, it will become the default one, so on next boot it will be used.
They also have a rollback mechanism with an ``health-checker``, a ``systemd`` service, which rollbacks to previous snapshot if something is wrong.
For transactional update, they rely on ``libtukit``.

They can also live apply the new snapshot, *i.e.* without rebooting, this is possible by moving all read-only parts to ``/usr``.
For ``/etc``, they use the ``overlayfs``.
But they need to deal with conflict in case a file exists in several layers.

They do not have any system configuration in ``/etc`` but in ``/usr``.
Only the admin changes are in ``/etc``, for example ``/etc/fstab``.
