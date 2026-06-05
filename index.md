---
layout: default
title: "ldx3 — Talks & Vendors"
description: "Conference talk notes and vendors-to-explore from LDX3."
---

{% comment %}
  Talks ordering: primary = date DESC (newest first); secondary = title ASC.

  Liquid's `sort` filter calls Ruby's Array#sort with a comparator block,
  which is NOT a stable sort, so chaining two `sort` calls cannot reliably
  deliver a stable secondary key. Instead we:
    1. Group talks by date (string-equal comparison).
    2. Sort the date groups by their `name` (the date string) DESC.
    3. Within each group, sort items by `title` ASC.
  Because each within-group sort happens on a distinct key (title) with no
  ties expected, stability doesn't matter inside the group.
{% endcomment %}

{% assign talks_by_date = site.talks | group_by_exp: "talk", "talk.date | date: '%Y-%m-%d'" %}
{% assign date_groups_sorted = talks_by_date | sort: "name" | reverse %}
{% assign reflections_by_date = site.reflections | group_by_exp: "r", "r.date | date: '%Y-%m-%d'" %}
{% assign reflection_date_groups_sorted = reflections_by_date | sort: "name" | reverse %}
{% assign vendors_sorted = site.vendors | sort: "title" %}

## Talks

<ul>
{% for date_group in date_groups_sorted %}
  {% assign items_sorted = date_group.items | sort: "title" %}
  {% for talk in items_sorted %}
  <li>
    <strong>{{ talk.date | date: "%Y-%m-%d" }}</strong> &middot;
    <a href="{{ talk.url | relative_url }}">{{ talk.title | escape }}</a> &middot;
    {{ talk.speaker | escape }}
    <br>
    <em>{{ talk.summary | escape }}</em>
  </li>
  {% endfor %}
{% endfor %}
</ul>

## Reflections

<ul>
{% for date_group in reflection_date_groups_sorted %}
  {% assign items_sorted = date_group.items | sort: "title" %}
  {% for reflection in items_sorted %}
  <li>
    <strong>{{ reflection.date | date: "%Y-%m-%d" }}</strong> &middot;
    <a href="{{ reflection.url | relative_url }}">{{ reflection.title | escape }}</a>
    <br>
    <em>{{ reflection.summary | escape }}</em>
  </li>
  {% endfor %}
{% endfor %}
</ul>

## Vendors to explore

<ul>
{% for vendor in vendors_sorted %}
  <li>
    <a href="{{ vendor.url | relative_url }}">{{ vendor.title | escape }}</a> &middot;
    <a href="{{ vendor.homepage | escape }}">{{ vendor.homepage | escape }}</a> &middot;
    seen at {{ vendor.seen_at | escape }}
    <br>
    <em>{{ vendor.summary | escape }}</em>
  </li>
{% endfor %}
</ul>
