Media Streaming Mesh (MSM)
--------------------------

We want to do real time on top of k8s particularly WebRTC (real time collaboration like FramaCalc).
From one input, we would like to create several output bitstreams (like one for each resolution).

The idea is to use pod sidecar.
MSM are written in go, can be deployed for each clusters and are compatible with several protocoles (*e.g.* SIP).
They also added a proxy to be able to communication with the MSM directly and not through the k8s proxy.
