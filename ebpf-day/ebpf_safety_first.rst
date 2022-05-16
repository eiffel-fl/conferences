eBPF? Safety first!
-------------------

This talk is about writing a proposal to use eBPF with rust.
Bu there is already the verifier which already enforces the memory access.
By using rust, the goal is to avoid sending, for example, bad events.

So, the support of generating eBPF code was added to `rustc` (*i.e.* the rust compiler).
They also use `libbpfgo` to use the object eBPF from golang.
