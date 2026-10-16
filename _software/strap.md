---
title: STRAP
description: >-
  Statistics TRAcking Protocol — a small, Unix-style text protocol for
  accumulating per-event statistics during scientific simulations, with a
  Rust-based GUI for visualizing the resulting data.
status: Experimental
role: Author
language: Rust (strap-gui), protocol specification
license: MIT
repo: "https://github.com/APN-Pucky/strap"
research_tags: [monte-carlo-software]
---

STRAP defines a simple, line-oriented text format for logging correlated
key/value statistics as a simulation runs — designed to be trivial to emit
from existing Fortran/C++ codes (e.g. by prefixing a log line with
`@strap`), mergeable across runs, and compressible for long jobs.

```
alice_sword 2.2
bob_bow 5.0
damage 2.0 attacker_alice 1.0 defender_bob 1.0
```

[`strap-gui`](https://github.com/APN-Pucky/strap-gui) is a Rust application
that visualizes STRAP-formatted data. This is an early-stage, experimental
protocol and tool, not yet used in a published physics analysis.
