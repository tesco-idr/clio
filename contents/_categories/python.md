---
layout: page
title: "Python"
---

{% for item in site.python %}
  <li><a href="{{ site.baseurl }}{{ item.url }}">{{ item.title }}</a></li>
{% endfor %}