---
title: LHEUTILS
description: >-
  Command-line utilities for filtering, converting and processing Les
  Houches Event (LHE) files and Monte Carlo event samples.
status: Active
role: Author
language: Python
license: Apache-2.0
repo: "https://github.com/APN-Pucky/lheutils"
install: "pip install lheutils"
research_tags: [monte-carlo-software]
---

A companion set of CLI tools to `pylhe` for everyday handling of LHE event
samples: filtering events by cuts, converting between formats, and
integrating with Python-based HEP analysis tools. Future development is
aimed at unweighting of filtered samples, additional file-format support,
and a faster Rust-based conversion pipeline, alongside tighter integration
with [pylhe]({{ '/software/pylhe/' | relative_url }}) and
[STRAP]({{ '/software/strap/' | relative_url }}).
