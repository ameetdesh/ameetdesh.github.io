---
layout: default
title: Writeups
permalink: /writeups/
description: Notes, papers and interactive tools on energy systems, optimization and market design.

# Anything that is not a Markdown note in this folder — PDFs, standalone tools —
# is listed by hand here. Add an entry and it appears below.
extras:
  - title: Smart Home Energy Optimizer
    subtitle: Battery, EV, water heater and air-conditioning dispatched together against solar output and a price signal. Runs entirely in the browser.
    url: /multi_device_optimizer_standalone.html
    date: August 2026
    tag: Interactive
  - title: Battery Optimizer
    subtitle: Single-device battery dispatch by dynamic programming, with a quiver overlay of the value function. Python via Pyodide, in the browser.
    url: /pyodide_optimizer_standalone.html
    date: August 2026
    tag: Interactive
  - title: Frequency Domain Control Design
    subtitle: Determining the optimal spectral response of a controller frequency by frequency, then realising it with a causal or limited-preview transfer function.
    url: /FreqDomDesign.pdf
    date: May 2026
    tag: PDF
---

Notes, papers and a few things you can run in the browser — mostly working
through a problem in public. Personal thought-exercises; they do not represent
the views of any organization I have worked for.

<ul class="entry-list">
{%- assign notes = site.pages | where_exp: "p", "p.path contains 'writeups/'" | where_exp: "p", "p.name != 'index.md'" | sort: "date" | reverse -%}
{%- for p in notes %}
  <li class="entry">
    <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
    {%- if p.subtitle %}
    <p class="summary">{{ p.subtitle }}</p>
    {%- endif %}
    {%- if p.date %}
    <p class="meta">{{ p.date | date: "%B %Y" }}</p>
    {%- endif %}
  </li>
{%- endfor %}
{%- for post in site.posts %}
  <li class="entry">
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {%- if post.subtitle %}<p class="summary">{{ post.subtitle }}</p>{% endif %}
    <p class="meta">{{ post.date | date: "%B %-d, %Y" }}</p>
  </li>
{%- endfor %}
{%- for x in page.extras %}
  <li class="entry">
    <a href="{{ x.url | relative_url }}">{{ x.title }}</a>{% if x.tag %}<span class="tag">{{ x.tag }}</span>{% endif %}
    {%- if x.subtitle %}
    <p class="summary">{{ x.subtitle }}</p>
    {%- endif %}
    {%- if x.date %}
    <p class="meta">{{ x.date }}</p>
    {%- endif %}
  </li>
{%- endfor %}
</ul>
