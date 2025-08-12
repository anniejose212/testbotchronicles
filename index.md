---
layout: default
title: TestBot Chronicles
---

# 🐞 TestBot Chronicles

Welcome to **TestBot Chronicles** — a knowledge hub for curious testers, QA enthusiasts, and anyone passionate about building better software.  
Here you’ll find **hands-on testing tips, real-world QA experiences, and deep dives** into manual testing, API automation, and DevOps practices.  

Whether you’re **debugging your first app** or **leading a complex test strategy**, this space is designed to help you level up — one post at a time.

---

## 📂 Explore by Category
- [Manual Mastery 🛠]({{ "/categories/manual-mastery/" | relative_url }})  
  *Core QA concepts, defect handling, and testing fundamentals.*

- [API Adventures 🔌]({{ "/categories/api-adventures/" | relative_url }})  
  *Learn how APIs work, Postman tips, and client-server basics.*

- [DevOps 🖥]({{ "/categories/devops/" | relative_url }})  
  *Configuration tips and why test vs prod matters.*
  
---

## 📝 Recent Posts
<ul>
{% for post in site.posts limit:12 %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span> — {{ post.date | date: "%b %d, %Y" }}</span>
    {% if post.categories and post.categories.size > 0 %}
      <em> · <a href="{{ '/categories/' | append: post.categories[0] | append: '/' | relative_url }}">{{ post.categories[0] }}</a></em>
    {% endif %}
  </li>
{% endfor %}
</ul>


## 👩‍💻 About Me

I'm a QA passionate about quality engineering and finding hidden bugs.  
This blog is my digital notebook — join me as I explore tools, test strategies, and practical examples from real projects.



*Built with 🧑‍💻📚🚀🌐  for continuous learning using GitHub Pages and the Cayman theme.*
