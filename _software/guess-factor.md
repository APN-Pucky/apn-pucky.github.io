---
title: guess_factor
description: >-
  Small C++ tool (with Python bindings) that guesses an unknown
  multiplicative factor between two numbers, by searching combinations of
  configurable bases (e.g. 2, π, 3, physics constants) raised to small
  integer exponents.
status: Active
role: Author
language: "C++, with Python bindings (pybind)"
license: GPL-3.0
repo: "https://github.com/APN-Pucky/guess_factor"
docs: "https://apn-pucky.github.io/guess_factor/index.html"
install: "cmake . && make"
---

Given a target number (and optionally a second number to divide it by
first), `guess_factor` searches products of configurable bases raised to
small integer exponents and reports the closest-matching combinations —
for example, recognizing that two numbers differ by `2 * π^2` or
`3^-1 * 2^4`. Bases and exponents are configurable at runtime
(`config.txt`) or compiled in for speed.

Originally a small standalone utility, it has been genuinely useful for
validating and cross-checking high-energy-physics codes against each
other: when two independent calculations of the same cross section or
distribution disagree by a constant factor rather than matching exactly,
`guess_factor` can often identify that factor automatically (a missing
`2π`, a spin/color-averaging factor, a unit-conversion constant), turning
a "why don't these two codes agree" debugging session into a quick,
mechanical check instead of a manual guess-and-check.
