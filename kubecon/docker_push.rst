From `docker push` to bytes on Disk
-----------------------------------

A registry is a place where container image are stored.

In the details, it is a content addressable object store.
It contains the following:

* blobs which are container layers.
* a manifest for a set of blobs
* several tags to identify images.

Inside `docker push`
====================

This talk focuses on CNCF Distribution which is a reference for container registry.
The layers are pushed first, then the manifest.
The digest of a blob if the hash of its content.
There are actually 3 ways to push a blob:

1. The Monolithic blob upload (now deprecated).
2. The Monolithic blob upload (new version and not deprecated).
3. The Chunked blob upload.

The last one initializes a session, upload the entire blob using HTTP PATCH and then their digest with HTTP PUT.

To use a blob from another repository (an image is a repository), for example because you use this blobl in your repository, you can mount it.
This way, it will avoid to push data to your repository.

Inside `docker pull`
====================

Pulling image is simpler than pushing one.
To get a blob, you just need to do an HTTP GET on the manifest, then on the image using its tag.

CNCF Distribution internals
===========================

Distribution is composed of the following components:

1. The HTTP API headers: It maps HTTP endpoints to given handlers.
2. The Open Container Initiative (OCI) abstractions: It contains a set of OCI abstractions to deal with container image.
3. A storage driver: It contains a set of functions to store the actual image to several targets (*e.g.* filesystem, aws, *etc.*).
3. The backend.

How bytes are written to the disk?
==================================

HTTP PATCH is composed of 3 steps:

1. The authentication.
2. The resume session which basically gives you a session ID.
3. The data upload where the PATCH body is copied to S3.

Then the storage driver is called.

Garbage collection
==================

The garbage collection targets the following:

* if a manifest does not have a corresponding tag, it is then garbage collected.
* blobs without a corresponding manifests can be garbage collected.

We need garbage collection because Distribution does not guarantee atomic operation.
