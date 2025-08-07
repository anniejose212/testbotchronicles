---
layout: default
title: blog
---

# 📝 Blog Posts

Welcome to the blog section of **TestBot Chronicles**. Here's a list of all my posts:

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small> - {{ post.date | date: "%B %d, %Y" }}</small>
    </li>
  {% endfor %}
</ul>
