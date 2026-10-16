---
title: pylhe
description: >-
  Lightweight, pure-Python library for reading and writing Les Houches
  Event (LHE) files, the standard Monte Carlo event format in high-energy
  physics. Part of the Scikit-HEP ecosystem.
status: Active
role: Core maintainer
language: Python
license: Apache-2.0
repo: "https://github.com/scikit-hep/pylhe"
docs: "https://pylhe.readthedocs.io/"
pypi: "https://pypi.org/project/pylhe/"
doi: "10.21105/joss.11128"
paper: "/publications/pylhe-joss/"
install: "pip install pylhe"
research_tags: [monte-carlo-software]
---

Reads `.lhe` and compressed `.lhe.gz` files, including LHE 3.0 features
(multiple event weights, generator metadata) and the HDF5-based LHEH5
format. Events are exposed through a pythonic iterator over shared data
structures, allowing large samples to be processed without loading an
entire file into memory, and can be converted into
[Awkward Array](https://awkward-array.org/) columnar structures for
downstream statistical and machine-learning analysis.

```python
import pylhe

events = pylhe.read_lhe("events.lhe.gz")
for event in events:
    for particle in event.particles:
        print(particle.id, particle.px, particle.py, particle.pz)
```

Originally developed independently, pylhe now lives under the
[Scikit-HEP](https://scikit-hep.org/) organisation and is described in a
peer-reviewed [JOSS paper]({{ '/publications/pylhe-joss/' | relative_url }})
co-authored with Matthew Feickert, Lukas Heinrich and Eduardo Rodrigues.
