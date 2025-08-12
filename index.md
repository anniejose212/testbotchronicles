---
layout: default
title: TestBot Chronicles
---

## 📂 Explore by Category

- [Manual Mastery 🛠](/categories/manual-mastery/)  
  *Core QA concepts, defect handling, and testing fundamentals.*

- [API Adventures 🔌](/categories/api-adventures/)  
  *Learn how APIs work, Postman tips, and client-server basics.*

- [DevOps 🖥](/categories/devops/)  
  *Configuration tips and why test vs prod matters.*
  
---

## 📝 Recent Posts

👉 
{% for post in site.posts limit:12 %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span> — {{ post.date | date: "%b %d, %Y" }}</span>
    {% if post.categories and post.categories.size > 0 %}
      <em> · <a href="{{ '/categories/' | append: post.categories[0] | append: '/' | relative_url }}">{{ post.categories[0] }}</a></em>
    {% endif %}
  </li>
{% endfor %}



## 👩‍💻 About Me

I'm a QA passionate about quality engineering and finding hidden bugs.  
This blog is my digital notebook — join me as I explore tools, test strategies, and practical examples from real projects.



*Built with 🧑‍💻📚🚀🐞  for continuous learning using GitHub Pages and the Cayman theme.*
