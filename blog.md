---
layout: page
title: Blog
---

_A collection of posts of variable length, detail, and lucidity. Most fall into the category of "Calculations and expositions I want immediate access to from anywhere with WiFi"._

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>


