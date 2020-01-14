---
layout: page
title: Archives
---

<ul id="archive">
{% for post in site.posts %}
<li>{{ post.date | date_to_string }} &mdash; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
