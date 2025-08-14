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

- [Automation Adventures 🔌]({{ "/categories/automation-adventures/" | relative_url }})  
  *Automation basics.*

- [DevOps 🖥]({{ "/categories/devops/" | relative_url }})  
  *Configuration/Operation tips.*
  
- [Real-World Test Cases 🧬]({{ "/categories/real-world-test-cases/" | relative_url }})  
  *Practical QA blueprints for testing success.*
  
---

## 📝 Recent Posts
<ul class="post-list">
  {% assign posts = site.posts | slice: 0, 12 %}
  {% for post in posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span> — {{ post.date | date: "%-d %b %Y" }}</span>
    </li>
  {% endfor %}
</ul>



## 👩‍💻 About Me

I'm a QA passionate about quality engineering and finding hidden bugs.  
This blog is my digital notebook — join me as I explore tools, test strategies, and practical examples from real projects.



*Built with 🧑‍💻📚🚀🌐  for continuous learning using GitHub Pages and the slate theme.*
