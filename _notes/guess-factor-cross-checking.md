---
title: Cross-checking HEP codes with guess_factor
date: 2026-10-26
tags: [validation, software, Monte Carlo]
description: >-
  How a small factor-guessing utility turns "why don't these two codes
  agree" into a quick, mechanical check instead of a manual search.
permalink: /notes/guess-factor-cross-checking/
---

Validating a new calculation against an existing one (a different
generator, a previous paper, an independent re-implementation) rarely ends
with the two numbers matching exactly on the first try. More often they
agree up to a constant: a missing `2π` from a phase-space measure, a
spin- or color-averaging factor, a units convention, a factor of 2 from
how an observable is symmetrized. Finding which constant explains the
discrepancy by hand means guessing combinations of small integers and
physical constants until something clicks.

[`guess_factor`](https://github.com/APN-Pucky/guess_factor) automates
exactly that search. Given a target ratio, it searches products of
configurable bases (`2`, `π`, `3`, and other physics constants, each with
its own set of allowed exponents) and reports the closest-matching
combinations, ranked by how well they reproduce the target. What used to
be "let me try dividing by a few powers of two and π and see if that
looks right" becomes a one-line lookup, and the output is explicit about
exactly which combination of bases and exponents was found, so the result
can be checked against the physics rather than taken on faith.

It has been genuinely useful in exactly this role: cross-checking
independent high-energy-physics codes against each other, where a
disagreement that first looks like a bug often turns out to be a known,
recoverable normalization difference once the missing factor is
identified.
