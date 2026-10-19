---
title: Talks
description: >-
  Conference talks, invited presentations and posters given by Alexander
  Puck Neuwirth on photon production, electromagnetic probes, Monte Carlo
  event generators and scientific software, 2022–2026.
permalink: /talks/
---

# Talks

Conference and workshop presentations, in reverse chronological order.
Also listed on [INSPIRE-HEP]({{ site.author.inspire_url }}) where indexed.

{% capture newline %}
{% endcapture %}
<ul class="card-list">
{% assign talks = site.data.talks | sort: "date" | reverse %}
{% for t in talks %}
  <li class="card">
    <h3>{{ t.event }}</h3>
    <p class="meta">{{ t.date_display }} · {{ t.role }}{% if t.location %} · {{ t.location }}{% endif %}</p>
    {% if t.title %}<p>&ldquo;{{ t.title }}&rdquo;</p>{% endif %}
    {% assign pub = nil %}
    {% if t.publication %}
      {% assign pub = site.publications | where: "slug", t.publication | first %}
    {% endif %}
    <p class="link-row">
      {% if t.url %}<a href="{{ t.url }}">Event page</a>{% endif %}
      {% if t.slides %}<a href="{{ t.slides | relative_url }}">Slides (PDF)</a>{% endif %}
      {% if pub %}<a href="{{ pub.url | relative_url }}">Related publication</a>{% endif %}
    </p>
    {% if t.abstract or pub.description %}
    <details>
      <summary>Abstract</summary>
      {% if t.abstract %}
        {% assign abstract_lines = t.abstract | strip | split: newline %}
        {% for line in abstract_lines %}{% if line != "" %}<p>{{ line }}</p>{% endif %}{% endfor %}
      {% else %}
        <p>{{ pub.description }}</p>
      {% endif %}
    </details>
    {% endif %}
  </li>
{% endfor %}
</ul>
