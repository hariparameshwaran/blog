---
layout: page
title: Series
permalink: /series/
---

{% assign series_posts = site.posts | where_exp: "post", "post.series" %}
{% assign series_names = series_posts | map: "series" | uniq %}

{% for s in series_names %}
  {% assign chapters = series_posts | where: "series", s | sort: "series_order" %}
  <h2>{{ chapters.first.series_title }}</h2>
  <ol>
    {% for post in chapters %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ol>
{% endfor %}
