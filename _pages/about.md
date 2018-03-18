---
permalink: /
title: "Minions currently building website"
excerpt: "About me"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

***Be right back.***

{% include base_path %}
{% capture written_year %}'None'{% endcapture %}
{% for post in site.posts %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% include archive-single.html %}
{% endfor %}
