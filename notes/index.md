---
title: Notes
description: >-
  Informal technical notes from Alexander Puck Neuwirth on particle-physics
  software and computation — work that does not always turn into a paper.
permalink: /notes/
---

# Notes

Shorter, less formal write-ups on tools, methods and in-progress work — the
parts of the job that do not always make it into a publication.

{% assign notes = site.notes | sort: "date" | reverse %}
<ul class="card-list">
{% for n in notes %}
  <li class="card">
    <h3><a href="{{ n.url | relative_url }}">{{ n.title }}</a></h3>
    <p class="meta"><time datetime="{{ n.date | date_to_xmlschema }}">{{ n.date | date: "%-d %B %Y" }}</time></p>
    <p>{{ n.description }}</p>
  </li>
{% endfor %}
</ul>
{% if notes.size == 0 %}
<p class="meta">No notes published yet — check back soon.</p>
{% endif %}
