---
layout: page
title: Tüm Bölümler
permalink: /arsiv/
---

Burada "Esrarın Hükümdarı" çevirisinin yayınlanmış tüm bölümlerini bulabilirsiniz.

<ul>
  {% for post in site.posts %}
    <li>
      <span style="color: #666; font-family: monospace;">[{{ post.date | date: "%d/%m/%Y" }}]</span>
      <a href="{{ post.url }}" style="font-weight: bold; margin-left: 10px;">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
