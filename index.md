---
title:
description: >-
  Alexander Puck Neuwirth is a theoretical and computational particle
  physicist at the University of Milano-Bicocca, working on perturbative
  QCD, electroweak corrections, photon production and Monte Carlo event
  generators.
permalink: /
wide: true
---

<div class="hero">
  <p class="meta">{{ site.author.job_title }} · {{ site.author.affiliation }}</p>
  <h1>Alexander Puck Neuwirth</h1>
  <p class="lede">
    Theoretical and computational particle physicist working on precision
    predictions for high-energy collisions: perturbative QCD and
    electroweak corrections, photon production, and Monte Carlo event
    generators.
  </p>
  <p>
    I am a {{ site.author.job_title | downcase }} in the
    {{ site.author.affiliation_department }} at the
    <a href="{{ site.author.affiliation_url }}">{{ site.author.affiliation }}</a>.
    I completed my PhD at the
    <a href="{{ site.author.previous_affiliation_url }}">{{ site.author.previous_affiliation }}</a>,
    where I worked on combining fixed-order QCD calculations with parton
    showers for real and virtual photon production. Alongside this
    research, I develop open-source scientific software
    (<a href="{{ '/software/pylhe/' | relative_url }}">pylhe</a>,
    <a href="{{ '/software/lheutils/' | relative_url }}">LHEUTILS</a>) and
    contribute to shared particle-physics infrastructure, including
    LHAPDF, HepMC, Rivet/YODA and Gentoo Linux.
  </p>
  <ul class="profile-links">
    <li><a href="https://orcid.org/{{ site.author.orcid }}">ORCID</a></li>
    <li><a href="{{ site.author.inspire_url }}">INSPIRE-HEP</a></li>
    <li><a href="{{ site.author.scholar_url }}">Google Scholar</a></li>
    <li><a href="{{ site.author.github }}">GitHub</a></li>
    <li><a href="{{ '/cv/' | relative_url }}" class="cv-download">Download CV (PDF)</a></li>
  </ul>
</div>

<div class="home-section-head">
  <h2>Research</h2>
  <a href="{{ '/research/' | relative_url }}">All research areas →</a>
</div>
<ul class="research-grid">
  <li>
    <h3><a href="{{ '/research/photon-fragmentation/' | relative_url }}">Photon Fragmentation Functions</a></h3>
    <p>Effective parton-to-photon fragmentation functions extracted from PYTHIA, distributed as LHAPDF grids.</p>
  </li>
  <li>
    <h3><a href="{{ '/research/low-mass-dileptons/' | relative_url }}">Low-Mass Dileptons</a></h3>
    <p>Virtual-photon conversion to lepton pairs: Kroll-Wada vs. parton-shower descriptions.</p>
  </li>
  <li>
    <h3><a href="{{ '/research/photon-jet-powheg/' | relative_url }}">Photon+Jet Production</a></h3>
    <p>NLO QCD photon-plus-jets predictions matched to parton showers via POWHEG and MiNLO.</p>
  </li>
</ul>

<div class="home-section-head">
  <h2>Selected publications</h2>
  <a href="{{ '/publications/' | relative_url }}">All publications →</a>
</div>
<ul class="card-list">
  {% assign featured = "photon-fragmentation-lhapdf,kroll-wada-dileptons,prompt-photon-two-jets-powheg,pylhe-joss" | split: "," %}
  {% for slug in featured %}
    {% assign p = site.publications | where: "slug", slug | first %}
    <li class="card">
      <h3><a href="{{ p.url | relative_url }}">{{ p.title }}</a></h3>
      <p class="meta">{{ p.authors | join: ", " }} · {% if p.venue %}{{ p.venue }}{% else %}{{ p.date | date: "%Y" }}{% endif %}</p>
    </li>
  {% endfor %}
</ul>

<div class="home-section-head">
  <h2>Software</h2>
  <a href="{{ '/software/' | relative_url }}">All software →</a>
</div>
<ul class="card-list">
  {% for s in site.software %}
    <li class="card">
      <h3><a href="{{ s.url | relative_url }}">{{ s.title }}</a></h3>
      <p>{{ s.description }}</p>
    </li>
  {% endfor %}
</ul>
