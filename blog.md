---
layout: cayman
title: Blog – TestBot Chronicles
url: /blog
---

# 📝 Blog Posts

Welcome to the blog section of **TestBot Chronicles** – where I share insights, tools, bugs, and testing experiences.

---

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> –
      <small>{{ post.date | date: "%B %d, %Y" }}</small>
    </li>
  {% endfor %}
</ul>
