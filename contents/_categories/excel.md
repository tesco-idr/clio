---
layout: page
title: "Excel"
---

{% for item in site.excel %}
  <li><a href="{{ site.baseurl }}{{ item.url }}">{{ item.title }}</a></li>
{% endfor %}
