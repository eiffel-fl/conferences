Containerd
----------

`containerd` has a year-to-year adaption growth of 500%.
`nerdctl` is a docker compatible CLI for `containerd`.
K8s uses `containerd`, so for each version of k8s there is a corresponding version of `containerd`, but not with the same version number.

`containerd` has several components, like a library, a client and `shim`.
Each component is, in its turn, divided in others components, *e.g* the library contains a resolver for image distribution.
Creating a container snapshot using the CLI results in going through different components and API.
For example, to pull an image from a registry:

* in case of a local image, the containerd API calls the local service.
* for a distant one, the shim API will pull it from you.

