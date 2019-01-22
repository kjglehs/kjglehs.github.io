---
layout: page
title: Laravel
---

<div class="posts">
  {% for post in site.categories.laravel %}
  <div class="post">
    <h1 class="post-title">
      <a href="{{ site.url }}/{{ post.url }}">
        {{ post.title }}
      </a>
    </h1>

    <span class="post-date">{{ post.date | date_to_string }}</span>

    <!--{{ post.content }}-->
  </div>
  {% endfor %}
</div>
