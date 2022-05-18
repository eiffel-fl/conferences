A deep dive into minikube!
--------------------------

Minikube was created in 2016 to help developer to setup a local k8s cluster.
Minikube testing was done on a dedicated hardware supporting nested virtualization.

Their flake test rate is about 10-15% which is quite high.
So, they built a tool to see if a test is flaky or not, this tool is built on top of `gopogh`.

`slowjam` is a tool which can be used to profile golang code.
`time-to-k8s` is a tool which measure the time for a cluster to be ready to run k8s.

k8s 1.24 removed using docker as container runtime, but it is a problem to use `minikube docker-env` which is 36 times faster compared to `docker load`.

You can use `minikube pause` to pause the k8s API server, but not the application.
It exists an addon, called auto-pause which tries to automate this.

Minikube benchmarks show how it competes well compared to others tools.

The minikube ISO might be migrated to its own repo.
Some users use minikube as a replacement for docker client by using `minikube start --no-kubernetes` which starts minikube without k8s.
This enables you to interact with the underlying container runtime.

Minikube, compared to others tools like `kind`, supports several container runtimes, while other only support `containderd`.

They recently added a `qemu` driver for arm64 on minikube beta as well as a GUI.

