---
layout: default
---

<h1>{{ page.title | default: "Category" }}</h1>

{% assign empty_array = "" | split: "" %}
{% assign target = page.category | default: "" %}

{% assign posts_in_cat = site.categories[target] | default: empty_array %}
{% assign posts_in_cat = posts_in_cat | sort: "date" | reverse %}

{% if posts_in_cat.size > 0 %}
  <ul>
  {% for post in posts_in_cat %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span> — {{ post.date | date: "%b %d, %Y" }}</span>
    </li>
  {% endfor %}
  </ul>
{% else %}
  <p>No posts in this category yet.</p>
{% endif %}


