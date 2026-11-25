---
title: Adding CUDA output to Symbolica
date: 2026-11-25
tags: [Symbolica, GPU, CUDA, Rust, symbolic computation]
description: >-
  A merged Symbolica pull request that generates CUDA kernels directly
  from symbolic expressions, for GPU-evaluating the large expressions
  produced by amplitude and loop-integral tools built on Symbolica.
permalink: /notes/symbolica-cuda-output/
---

[Symbolica](https://symbolica.io/) compiles symbolic expressions down to
optimized native code for fast repeated numerical evaluation; until
recently that meant C++ or native Rust. [PR #30 on
symbolica-dev/symbolica](https://github.com/symbolica-dev/symbolica/pull/30)
(merged) adds a CUDA backend to that same code-generation path, so an
expression can be evaluated on a GPU instead.

Getting there meant working through CUDA's specific constraints rather
than reusing the CPU path unchanged: complex-number arithmetic has to go
through `cuDoubleComplex`/`std::cuda::complex` instead of the host-side
complex type, generated functions are named by a mangled signature so
loading a compiled kernel is type-checked rather than taking the caller's
word for it, and the generic `Library<T>` wrapper is reused across calls
instead of recompiling, since each compile is expensive and GPU memory is
the constrained resource. CUDA resources are released deterministically
through a `Drop` implementation rather than left to whenever the host
process happens to clean up. Validation compared single-point and batched
evaluation against the existing CPU path, and checked that CUDA
evaluation can run correctly from both Rust and Python callers in
parallel, before any of it touches a performance claim.

The expressions this matters for — squared matrix elements, loop-integral
reduction tables — are exactly what the current crop of Rust-based,
Symbolica-backed tools spend most of their runtime evaluating:
[alphaLoop](https://github.com/alphal00p)'s stack (`rustred`, a LiteRed
port; `oneloopmaster`; `gammaloop`; `RustFlow`) and tree-level generators
such as [pyAmpliCol](https://arxiv.org/abs/2610.10729) all hit the same
bottleneck of evaluating very large symbolic expressions numerically,
many times over, at scale. A CUDA backend in Symbolica itself means any
of them can move that evaluation onto a GPU without building and
maintaining their own code-generation layer to do it.
