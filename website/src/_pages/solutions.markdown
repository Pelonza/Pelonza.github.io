---
title: Lab Solutions
layout: content
permalink: /solutions/index.html
---

{% for post in site.solutions %}
+   [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}
