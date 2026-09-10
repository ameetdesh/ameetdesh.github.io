---
layout: default
title: Writeups
permalink: /writeups/
description: Long-form notes on energy systems, optimization and market design.
---

Longer notes, mostly working through a problem in public. Personal
thought-exercises — they do not represent the views of any organization I have
worked for.

<ul class="entry-list">
{%- assign entries = site.pages | where_exp: "p", "p.path contains 'writeups/'" | where_exp: "p", "p.name != 'index.md'" | sort: "date" | reverse -%}
{%- for p in entries %}
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
{%- if site.posts.size > 0 %}
{%- for post in site.posts %}
  <li class="entry">
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {%- if post.subtitle %}<p class="summary">{{ post.subtitle }}</p>{% endif %}
    <p class="meta">{{ post.date | date: "%B %-d, %Y" }}</p>
  </li>
{%- endfor %}
{%- endif %}
</ul>
