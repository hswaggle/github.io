---
layout: page
title: Prose
permalink: /prose/
---

{% assign poetry_posts = site.posts | where_exp: "item", "item.tags contains 'poetry'" %}
{% for post in poetry_posts %}
  <article class="feed-item d-flex justify-content-between align-items-center mb-4">
    <div class="flex-grow-1 pe-3">
      <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      {% if post.subtitle %}
        <h4>{{ post.subtitle }}</h4>
      {% endif %}
      <p class="post-meta">
        {{ post.date | date: "%B %-d, %Y" }}{% if post.author %} — {{ post.author }}{% endif %}
      </p>
      <p>{{ post.excerpt }}</p>
    </div>

    {% if post.thumbnail-img %}
      <div class="flex-shrink-0" style="max-width: 150px;">
        <a href="{{ post.url | relative_url }}">
          <img src="{{ post.thumbnail-img | relative_url }}" alt="Thumbnail for {{ post.title }}" class="img-fluid rounded">
        </a>
      </div>
    {% endif %}
  </article>
  <hr />
{% endfor %}
