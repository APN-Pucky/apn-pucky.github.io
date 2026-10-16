---
title: Why prompt-photon predictions still need fragmentation functions
date: 2026-08-20
tags: [photon production, QCD, LHAPDF]
description: >-
  A plain-language look at why isolated prompt-photon measurements still
  depend on parton-to-photon fragmentation, and what a PYTHIA-based
  extraction adds.
permalink: /notes/photon-fragmentation-why-it-matters/
---

Prompt photons — photons produced directly in a hard partonic scattering —
are one of the cleanest handles we have on the gluon and quark content of
colliding protons and nuclei. In practice, experiments never measure a
purely "direct" photon: a quark or gluon can radiate a photon collinearly
as it fragments, and an isolation cut (removing hadronic activity near the
photon) only suppresses this fragmentation contribution, it does not
eliminate it.

That residual piece is controlled by parton-to-photon fragmentation
functions, and the standard sets used to describe them (BFG, GRV, GDRG)
are decades old fits with only loose experimental constraints. In
[arXiv:2608.15944]({{ '/publications/photon-fragmentation-lhapdf/' | relative_url }})
I took a more pragmatic route: rather than fitting data directly, extract
an effective fragmentation function straight from PYTHIA's own parton
shower, flavour by flavour, and package it as an LHAPDF grid so it can be
dropped into existing fixed-order codes exactly like any other
fragmentation set. Along the way, converting the legacy BFG/GRV/GDRG sets
into the same LHAPDF grid format turned up a more mundane but useful
finding: LHAPDF's default log-cubic interpolation reproduces the
tabulated functions noticeably better than the linear interpolation used
in older, hand-rolled implementations — a reminder that infrastructure
choices (interpolation, grid spacing) can matter as much as the physics
input itself.

See the [photon fragmentation research page]({{ '/research/photon-fragmentation/' | relative_url }})
for where this is headed next.
