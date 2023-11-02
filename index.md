---
layout: default
title: Home
---
<div class="mt-1 row row-cols-1 row-cols-md-3 g-4">
  {% for post in site.posts %}
  <div class="col">
    <div class="card text-center">
  <div class="card-header">
    <h5 class="card-title post-title">{{ post.title }}</h5>
  </div>
  <div class="card-body">
    <p class="card-text">{{ post.excerpt }}</p>
    <a href="{{ post.url }}" class="btn btn-dark">Read more...</a>
  </div>
  <div class="card-footer text-body-secondary">
    {{ post.date | date: "%b %d, %Y" }}
  </div>
</div>
</div>
  {% endfor %}
</div>
