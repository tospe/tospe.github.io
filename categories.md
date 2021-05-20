---
layout: page
title: Categories
permalink: /categories/
---
 {% for tag in site.categories %}
  <h6>{{ tag[0] }} ({{tag[1]|size}})</h6>
  <ul>
    {% for post in tag[1] %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
  {% endfor %}