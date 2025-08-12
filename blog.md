---
layout: default
title: Basics
permalink: /basics/
description: ""
---


{% if site.posts and site.posts.size > 0 %}
  <ul style="list-style: none; padding-left: 0;">
  {% for post in site.posts %}
    <li style="margin-bottom: 1.5rem;">
      <h2 style="margin-bottom: 0.2rem;">
        <a href="{{ post.url | relative_url }}" style="text-decoration: none; color: #0366d6;">
          {{ post.title }}
        </a>
      </h2>
      <small style="color: #666;">{{ post.date | date: "%d %b %Y" }}</small>
      {% if post.excerpt %}
        <p style="margin-top: 0.5rem;">
  {{ post.excerpt | replace: "Content:", "" | strip_html | truncate: 160 }}
</p>
      {% endif %}
    </li>
  {% endfor %}
  </ul>
{% else %}
  <p>No posts yet. Add files to <code>_posts/</code> like <code>2025-08-07-my-first-post.md</code>.</p>
{% endif %}

