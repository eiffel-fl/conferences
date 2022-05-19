Reproducing Production Issues in your CI Pipeline Using eBPF
------------------------------------------------------------

Traffic mirroring, as used by Twitter, consist in mirrorgin the traffic to several pods in production.
Traffic replay uses a PV to copy the traffic from production to the test environment.
This permits having realistic network traffic.

Pixie enables users to probe the TLS libraries (*e.g.* `openssl`).

You can interact with Pixie with:
1. A gRPC API.
2. A plug-in system.

The demo use cases is about to test the API contract is still correct and that new version is not slower than previous.
There is a tool called `pixie-to-curl` to translate requests done on pixie to a bash script containing `curl` calls.
