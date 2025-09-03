---
layout: page
title: In Search of Moderates
permalink: /climbing/
cover-img: /assets/img/ism/Evergreen.JPEG
hidden: true
---

When I started climbing I dreamt of a gradual progression towards harder and harder goals. The movies I watched, the books I read, we're usually focused on the hardest of hard ascents. Aesthetic nearly impossible lines, grand adventures, some derived achievement beyond the summit. At the same time as it has become gradually clear that I will never be a great climber, the aesthetic and the difficult have become disentagled. I've done more beautiful classics under 5.5 in the last few years then I did in my summer of "grade pushing". I find myself more and more searching out great adventures, with aesthethic lines, yet objectively moderate routes. 

While climbing in the rockies, penned in by high avalanche risk, contained to a ice crag aptly named *Junkyards*, I found while briefly off route a ~luggage tag inscribed with a poem. 

<img src="{{ '/assets/img/ism/found_poem.jpg' | relative_url }}" 
     alt="Found Poem" 
     class="mx-auto d-block" 
     style="transform: rotate(90deg); max-width: 100%; height: auto;" />

It reads:
    
In the winter of 2021-22, Toronto got about 2-3 feet of snow overnight, reeling from the social absence of a now slightly less strict lockdown. I called two of my buddies to see if they wanted to try to ski at the Brickworks, a historic quarry that has been 90 percent filled in but still offers ~60-70 metres of verticality. Up we went, post-holing through the new snow. At the top, a variety of lines presented themselves, from moderate to steep. Our first lap we realized, the fresh snow had no base layer to protect our skiis from the brick paded hills beneath. What at best could be described as a moderate franken-backcity descent, proved to be a boatload of fun. 

In this, I found an ethic.

*Search out beauty, and joy, and moderates, and if you are lucky find them all at once.*

![Evergreen]({{ 'assets/img/ism/Evergreen.JPEG' | relative_url }}){: .mx-auto.d-block :}

{% assign cl_posts = site.posts | where_exp: "item", "item.tags contains 'climbing'" %}
{% for post in cl_posts %}
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

