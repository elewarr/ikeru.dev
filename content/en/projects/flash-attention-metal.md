---
title: "Flash Attention for Apple Silicon"
description: "A port of Flash Attention to Apple Silicon via Metal — enabling efficient transformer attention on M1/M2/M3/M4 Macs."
weight: 3
---

## Flash Attention for Apple Silicon

[Flash Attention](https://github.com/Dao-AILab/flash-attention) is a landmark algorithm by Tri Dao for computing exact scaled dot-product attention in transformers with O(N) memory instead of the naive O(N^2). It's used by virtually every major AI lab and has become the de facto standard for efficient attention in modern LLMs.

The original implementation targets NVIDIA CUDA GPUs. This fork adds a **native Apple Silicon Metal backend**, bringing Flash Attention to M1/M2/M3/M4 Macs with zero code changes required from the user.

{{< spacer >}}

## The Port

The Metal backend takes a different approach from the CUDA implementation. Instead of C++ extensions compiled with nvcc, the port generates Metal Shading Language (MSL) kernels at runtime as Python strings and compiles them via Apple's Metal API through PyObjC bindings. No C/C++ build step is needed on Mac.

This gives fine-grained control over compute pipelines, buffer management, and threadgroup configuration — while keeping the install as simple as `pip install`.

{{< spacer >}}

{{< cards count=3 >}}
{{< card >}}
### Drop-in Compatible
Same function signatures as the CUDA backend. Existing code using `flash_attn_func()` works transparently on Apple Silicon with zero changes. Auto-detects MPS devices.
{{< /card >}}
{{< card >}}
### Direct Metal API
Uses the raw Metal API via PyObjC rather than higher-level frameworks. MSL kernels implement the full Flash Attention algorithm: tiled computation, online softmax, causal masking.
{{< /card >}}
{{< card >}}
### Kernel Caching
Two-tier compilation cache — runtime MTLLibrary and pre-compiled `.metallib` via Xcode toolchain. Cache keys account for source hash, device, macOS version, and package version.
{{< /card >}}
{{< /cards >}}

{{< spacer >}}

## Supported Features

- **Forward and backward pass** in fp16
- **Head dimensions** 64, 128, and 256
- **Causal masking** and non-causal attention
- **Multi-query and grouped-query attention** (MQA/GQA)
- **Sequence lengths** up to 8192
- **All Apple Silicon generations** — M1, M2, M3, M4
- **Graceful fallback** — unsupported features (dropout, ALiBi, sliding window) fall back to PyTorch's native SDPA with a warning rather than crashing

{{< spacer >}}

## How the Kernels Work

The forward kernel implements the standard Flash Attention algorithm with online softmax:

1. Load a block of Q rows into registers
2. Iterate over K/V blocks in threadgroup (shared) memory
3. Compute attention scores with optional causal masking
4. Online softmax — track running max and sum, apply correction factors
5. Accumulate the output and normalize

The backward pass uses a three-kernel approach: delta preprocessing, dQ computation, and joint dK/dV computation — all with recomputation from saved log-sum-exp values rather than materializing the full attention matrix.

{{< spacer >}}

## Tech Stack

Built with Python and Metal Shading Language. GPU compute runs through Apple's Metal framework via PyObjC bindings, with tensors on PyTorch's MPS backend. The kernel generator is based on [philipturner/metal-flash-attention](https://github.com/philipturner/metal-flash-attention) as a reference implementation.

## Links

- [GitHub repository](https://github.com/elewarr/flash-attention) (public)
- [Upstream: Dao-AILab/flash-attention](https://github.com/Dao-AILab/flash-attention)
- [Flash Attention paper (arXiv:2205.14135)](https://arxiv.org/abs/2205.14135)

## License

BSD 3-Clause, following the upstream project.
