---
layout: page
title: Prose
permalink: /prose/
---

<div class="feed-posts">
  {% for post in site.posts %}
    <article class="feed-item">
      <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      {% if post.subtitle %}
        <h4>{{ post.subtitle }}</h4>
      {% endif %}
      <p class="post-meta">
        {{ post.date | date: "%B %-d, %Y" }}{% if post.author %} — {{ post.author }}{% endif %}
      </p>
      <p>{{ post.excerpt }}</p>
    </article>
    <hr />
  {% endfor %}
</div>
