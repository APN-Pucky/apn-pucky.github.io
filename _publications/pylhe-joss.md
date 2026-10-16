---
slug: pylhe-joss
title: "pylhe: A Lightweight Python Interface to Les Houches Event Files"
authors:
  - Alexander Puck Neuwirth
  - Matthew Feickert
  - Lukas Heinrich
  - Eduardo Rodrigues
venue: "Journal of Open Source Software, 11(126), 11128"
date: 2026-07-31
doi: "10.21105/joss.11128"
arxiv: "2607.29352"
status: Published
code: "https://github.com/scikit-hep/pylhe"
research_tags: [monte-carlo-software]
description: >-
  Les Houches Event files are a standard format for Monte Carlo event
  generators in high-energy physics. pylhe is a pure-Python library for
  reading and writing LHE event data, supporting .lhe and compressed .lhe.gz
  files, the widely used LHE 3.0 features including multiple event weights
  and generator metadata, and the recent HDF5-based LHEH5 format. By exposing
  events through a pythonic iterator and shared data structures, pylhe
  enables memory-efficient processing of large event samples without loading
  entire files into memory, and supports format conversion and integration
  with modern analysis workflows, including columnar analysis with Awkward
  Array and downstream machine-learning applications.
---

Part of the [Scikit-HEP](https://scikit-hep.org/) ecosystem. See the
[pylhe software page]({{ '/software/pylhe/' | relative_url }}) for
installation instructions and example usage.
