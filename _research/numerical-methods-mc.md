---
title: Numerical Methods for Monte Carlo Event Generators
description: >-
  Computational and numerical-methods research around Monte Carlo event
  generation: adaptive integration, rejection sampling, and scientific
  computing for NLO/NNLO-matched generators.
status: Exploratory
slug: numerical-methods-mc
permalink: /research/numerical-methods-mc/
---

Monte Carlo event generators such as POWHEG rely on adaptive integration
and rejection sampling to turn differential cross sections into unweighted
events. The efficiency of rejection sampling depends directly on how tight
an upper bound can be constructed for the event-generation probability;
poor bounds translate into wasted computing time. I am interested in how
modern numerical and machine-learning methods — from tree-based models to
simple surrogate models — could improve upper-bound construction and
sampling efficiency in this setting, as well as in GPU acceleration and
parallel evaluation of matrix elements more broadly.

This is an active area of methodological exploration rather than a line of
published results. Concrete findings will be added here, with code and
benchmarks, once they are reproducible and public.
