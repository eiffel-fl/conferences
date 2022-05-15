Now what we can checkpoint containers, what's next?
---------------------------------------------------

This talk focuses on CRIU (Checkpoint/Restore In Userspace).
CRIU is used to enable container live migration with `openVZ`, `borg`, `docker`, `podman`, *etc.*.
The integration withing CRI-O is in progress as an opened pull request while it is an issue in k8s.

Checkpointing containers have different use cases:

1. Avoid the time to boot the container and/or the underlying host.
2. Migrate a container from one host to another.

The plans to be dissuced with the community are:

1. Add a `kubectl checkpoint`.
2. Add a `kubectl migrate`.
3. Modify pod scheduler.
