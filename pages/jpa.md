---
layout: page
title: JPA
---

<div class="posts">
  {% for post in site.categories.jpa %}
  <div class="post">
    <h1 class="post-title">
      <a href="{{ site.url }}{{ post.url }}">
        {{ post.title }}
      </a>
    </h1>

    <span class="post-date">{{ post.date | date_to_string }}</span>
  </div>
  {% endfor %}
</div>