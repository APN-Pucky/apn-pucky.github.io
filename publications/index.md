---
title: Publications
description: >-
  Peer-reviewed publications, preprints and the doctoral thesis of
  Alexander Puck Neuwirth, in perturbative QCD, electroweak corrections,
  photon production and Monte Carlo event generators.
permalink: /publications/
---

# Publications

Also indexed on [INSPIRE-HEP]({{ site.author.inspire_url }}) and
[ORCID](https://orcid.org/{{ site.author.orcid }}), which are kept as the
authoritative record.

{% assign pubs = site.publications | sort: "date" | reverse %}
<ul class="card-list">
{% for p in pubs %}
  <li class="card">
    <h3><a href="{{ p.url | relative_url }}">{{ p.title }}</a></h3>
    <p class="meta">{{ p.authors | join: ", " }}</p>
    <p class="meta">
      {% if p.venue %}{{ p.venue }}{% endif %}
      {% if p.status %} · <span class="status-badge{% if p.status == 'Preprint' %} is-active{% endif %}">{{ p.status }}</span>{% endif %}
    </p>
    <p class="link-row">
      {% if p.arxiv %}<a href="https://arxiv.org/abs/{{ p.arxiv }}">arXiv:{{ p.arxiv }}</a>{% endif %}
      {% if p.doi %}<a href="https://doi.org/{{ p.doi }}">DOI</a>{% endif %}
    </p>
  </li>
{% endfor %}
</ul>
