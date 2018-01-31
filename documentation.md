---
layout: default
title: Docs
permalink: /documentation/
---

Documentation of our efforts to reverse engineer the John Deere CAN bus protocol can be found here.

{% for item in site.documentation %}
  <h2>{{ item.title }}</h2>
  <p>{{ item.description }}</p>
  <p><a href="{{ item.url }}">{{ item.title }}</a></p>
{% endfor %}
