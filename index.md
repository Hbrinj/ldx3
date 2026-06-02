---
title: "ldx3 — Talks & Vendors"
---

# ldx3 — Talks & Vendors

Conference talk notes and vendors-to-explore from LDX3.

{% comment %}
  Talks ordering: primary = date DESC (newest first); secondary = title ASC.
  Liquid's `sort` is stable. To get title ASC within same-date groups after the
  final reverse, we pre-sort by title DESC (sort then reverse), then sort by
  date ASC (stable: keeps the title-DESC order for ties), then reverse the
  whole list. The reverse flips dates to DESC and, because the within-date
  order was DESC, also flips ties back to ASC. Net result: newest date first,
  alphabetical (A→Z) within a date.
{% endcomment %}
{% assign talks_by_title_desc = site.talks | sort: "title" | reverse %}
{% assign talks_sorted = talks_by_title_desc | sort: "date" | reverse %}
{% assign vendors_sorted = site.vendors | sort: "title" %}

## Talks

<ul>
{% for talk in talks_sorted %}
  <li>
    <strong>{{ talk.date | date: "%Y-%m-%d" }}</strong> &middot;
    <a href="{{ talk.url | relative_url }}">{{ talk.title }}</a> &middot;
    {{ talk.speaker }}
    <br>
    <em>{{ talk.summary }}</em>
  </li>
{% endfor %}
</ul>

## Vendors to explore

<ul>
{% for vendor in vendors_sorted %}
  <li>
    <a href="{{ vendor.url | relative_url }}">{{ vendor.title }}</a> &middot;
    <a href="{{ vendor.homepage }}">{{ vendor.homepage }}</a> &middot;
    seen at {{ vendor.seen_at }}
    <br>
    <em>{{ vendor.summary }}</em>
  </li>
{% endfor %}
</ul>
