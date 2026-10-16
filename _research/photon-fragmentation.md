---
title: Photon Fragmentation Functions
description: >-
  Extracting effective photon fragmentation functions from PYTHIA parton
  showers and distributing them as LHAPDF grids, for use in prompt-photon
  predictions.
status: Active
slug: photon-fragmentation
permalink: /research/photon-fragmentation/
---

Photon fragmentation functions describe the production of photons through
the fragmentation of energetic quarks and gluons, and are a necessary
ingredient in theoretical predictions for prompt-photon production once
experimental isolation criteria are applied. Traditional parametrizations
(BFG, GRV, GDRG) date back to fixed-order fits and are only weakly
constrained by data.

This project investigates the extraction of effective photon fragmentation
functions directly from the PYTHIA parton shower, via a dedicated
[Rivet](https://rivet.hepforge.org/) analysis (`MC_PHOTONFRAGMENTATION`)
that records the flavour-dependent fragmentation distributions as a
function of the photon momentum fraction and fragmentation scale,
separately for quark and gluon channels. The resulting shower-level
estimates are exported as [LHAPDF](https://www.lhapdf.org/)-compatible
grids, alongside LHAPDF conversions of the existing BFG, GRV and GDRG sets,
enabling a direct, like-for-like comparison of interpolation behaviour,
kinematic endpoints and low-z behaviour between the shower extraction and
legacy parametrizations.

## Published results

- [Photon Fragmentation Functions in LHAPDF: Existing Sets and a Pythia-Based Extraction]({{ '/publications/photon-fragmentation-lhapdf/' | relative_url }}) (arXiv:2608.15944)

## Ongoing and future work

- Effective nonperturbative boundary conditions informed by the PYTHIA
  extraction.
- Investigation of factorization-scheme differences (MS-bar vs. DIS-γ).
- Evolution studies using APFEL++ and GEKO.
- Comparisons with photon-in-jet observables in $e^+e^-$ and $ep$ collisions.
