---
title: A common Rivet validation layer across POWHEG, GENEVA, MCFM and JetPhox
date: 2026-10-16
tags: [Monte Carlo, Rivet, validation, software]
description: >-
  Notes on building Rivet/HepMC interfaces for several otherwise
  incompatible fixed-order and parton-shower codes, so their predictions
  can be validated and cross-compared through one analysis layer.
permalink: /notes/rivet-validation-interfaces/
---

**POWHEG ↔ Pythia/Herwig ↔ Rivet.** POWHEG generates events as Fortran
common blocks (`HEPEUP`); Rivet expects a C++ `AnalysisHandler` fed HepMC
events. The interface sits directly on that boundary, converting POWHEG's
native event record into HepMC for Pythia 6, Pythia 8.2/8.3 or Herwig 7
indiscriminately through one abstraction layer, with explicit staging for
POWHEG-BOX-RES's multi-stage radiation generation (separate hooks for the
Born-level, first-radiation and shower-matched stages) so a Rivet analysis
can run at whichever stage is actually needed. It also taps directly into
POWHEG's native reweighting infrastructure (`pwhg_weights`), so scale- and
PDF-variation weights registered by POWHEG propagate through as proper
multi-weight Rivet/YODA histograms rather than single central-value
curves — the uncertainty bands are real, not bolted on afterwards.

**Upstream ALICE analyses.** Several of the analyses these interfaces run
are not just used but authored and merged directly into
[Rivet](https://gitlab.com/hepcedar/rivet) itself:
[ALICE_2025_I2895564](https://gitlab.com/hepcedar/rivet/-/merge_requests/1233)
(isolated prompt photon production in pp and p-Pb),
[ALICE_2024_I2803487](https://gitlab.com/hepcedar/rivet/-/merge_requests/1192)
and
[ALICE_2019_I1738300](https://gitlab.com/hepcedar/rivet/-/merge_requests/1164)
(inclusive isolated photon production at 13 and 7 TeV), and
[ALICE_2020_I1797621](https://gitlab.com/hepcedar/rivet/-/merge_requests/1187)
and
[ALICE_2018_I1672792](https://gitlab.com/hepcedar/rivet/-/merge_requests/1193)
(di-electron production in pp and p-Pb) — plus assorted validation fixes to
several other ALICE analyses already in the library. These are exactly the
observables (isolated photons, low-mass dielectrons) the research on this
site is about, now available to anyone running Rivet, not just internally.

**GENEVA validation.** Validating GENEVA's NNLO-QCD + NLO-EW Drell-Yan
predictions means checking several perturbative combinations (NLO and
NNLO QCD, with and without NLO electroweak and photon-induced
contributions) at two LHC energies against each other and against
published measurements. The validation analysis books every observable
twice — once at the nominal order and once as an explicit NNLO-QCD
variant with matching binning — and several histograms are booked with
bin edges taken directly from specific figures in published papers, so
the generated distributions overlay the original plots exactly rather
than needing to be rebinned by eye afterwards.

**MCFM and JetPhox.** MCFM books histograms through its own internal
"nplotter" system, not Rivet; a small converter exposes the same
differential information as a proper Rivet analysis instead, which is
what made it possible to cross-check the photon-fragmentation extraction
against MCFM on equal footing. JetPhox has a similar gap on the output
side: it writes events to ROOT ntuples rather than any event-record
format Rivet understands, so a converter turns those ntuples into HepMC3
events, letting unmodified, standard Rivet analyses run on JetPhox
predictions directly.
