---
layout: page
title: Tags
permalink: /tags/
---

{%- comment -%} 顶部标签云快速跳转 {%- endcomment -%}
<div style="margin-bottom: 24px;">
  {% for tag in site.tags %}
    {% assign tag_name = tag[0] %}
    <a href="#{{ tag_name | slugify }}" style="margin-right: 12px; display: inline-block;">
      #{{ tag_name }} ({{ tag[1].size }})
    </a>
  {% endfor %}
</div>

<hr>

{%- comment -%} 按标签分组列出对应文章 {%- endcomment -%}
{% for tag in site.tags %}
  {% assign tag_name = tag[0] %}
  <h3 id="{{ tag_name | slugify }}" style="margin-top: 24px;">#{{ tag_name }}</h3>
  <ul>
    {% for post in tag[1] %}
    <li>
      <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span> — 
      <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
    </li>
    {% endfor %}
  </ul>
{% endfor %}
