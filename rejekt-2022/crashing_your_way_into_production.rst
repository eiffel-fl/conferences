Crashing your way into production
---------------------------------

There are a lot of people working at CERN and then a lot of services.
The CERN website was hosted on VM and the goal is to containerize it.

The authors had a problem with CephFS where there were peak of requests.
The problem was linked to SELinux mount option and was fixed to upstream CephFS.

They the had events which were frozen with a specific kernel version.
With the new infrastructure, the performance were degraded compared to the old one but they found the root cause.
Velero cannot be used for backup no more because it takes a lot of time, so they made it parallel.
