---
title: Software
description: >-
  Open-source scientific software authored and maintained by Alexander Puck
  Neuwirth for high-energy physics event generation, data processing and
  packaging, including pylhe, LHEUTILS and STRAP.
permalink: /software/
---

# Software

I develop and maintain open-source tools for Monte Carlo event generation
and particle-physics data analysis, and contribute to community
infrastructure that this software relies on:

- Code contributor to [LHAPDF](https://www.lhapdf.org/), the standard
  library for accessing parton distribution functions at the LHC.
- Contributor to [HepMC](https://gitlab.cern.ch/hepmc/HepMC3), the common
  event-record format shared by Monte Carlo generators, and to
  [Rivet](https://rivet.hepforge.org/) and [YODA](https://yoda.hepforge.org/),
  used for analysis and histogramming of generated events.
- [Gentoo Linux](https://www.gentoo.org/) developer
  ([wiki profile]({{ site.author.gentoo_wiki }})), maintaining scientific
  packages in the [`gentoo-sci`](https://github.com/gentoo/sci) overlay —
  see the full, live list on [Repology]({{ site.author.repology_url }}).
- Active in the [Scikit-HEP](https://scikit-hep.org/) ecosystem, primarily
  through `pylhe`.

## Projects

<ul class="card-list">
{% assign tools = site.software | sort: "title" %}
{% for s in tools %}
  <li class="card">
    <h3><a href="{{ s.url | relative_url }}">{{ s.title }}</a></h3>
    <p class="meta">
      <span class="status-badge{% if s.status == 'Active' %} is-active{% endif %}">{{ s.status }}</span>
      {% if s.role %} · {{ s.role }}{% endif %}
    </p>
    <p>{{ s.description }}</p>
    <p class="link-row">
      {% if s.repo %}<a href="{{ s.repo }}">Source</a>{% endif %}
      {% if s.docs %}<a href="{{ s.docs }}">Docs</a>{% endif %}
      {% if s.pypi %}<a href="{{ s.pypi }}">PyPI</a>{% endif %}
      {% if s.doi %}<a href="https://doi.org/{{ s.doi }}">DOI</a>{% endif %}
    </p>
  </li>
{% endfor %}
</ul>
