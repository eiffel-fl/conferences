Supply chain
------------

Supply chain attacks inceased from 650% in 2021 compared to 2020.

If you are administration of a cluster, you should ask yourself the following:

1. Do you know what is running in your cluster (what the images are, who created them and how old they are)
2. Can you prove it?

Signing container images can help us answer these questions.
To do so, you can use:

1. Notary.
2. Sigstore.

With Sigstore, the signatures are stored in registry and it is a Linux Foundation project.
`cosign` (a toll from Sigstore) can be used to generate a pair of key to sign a container image (the image have to be available online).
The signature will be then pushed to the docker hub as a blob to which you can add annotations (*e.g.* to indicate the image is a production one).

Kyverno can enforce that all images in a cluster are signed.
