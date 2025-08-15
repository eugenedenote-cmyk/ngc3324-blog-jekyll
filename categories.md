---
layout: page
title: 카테고리
permalink: /categories/
---

<div class="category-list">
  {% assign categories = site.categories | sort %}
  {% for category in categories %}
    <div class="category-item">
      <h3 id="{{ category[0] | slugify }}">
        <a href="#{{ category[0] | slugify }}">{{ category[0] }}</a>
        <span class="category-count">({{ category[1].size }})</span>
      </h3>
      <ul class="post-list">
        {% assign posts = category[1] | sort: 'date' | reverse %}
        {% for post in posts %}
          <li>
            <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
            <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
</div>

<style>
.category-list {
  margin: 2rem 0;
}

.category-item {
  margin-bottom: 2rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #e8e8e8;
}

.category-item h3 {
  color: #1565c0;
  margin-bottom: 1rem;
}

.category-count {
  color: #666;
  font-size: 0.9rem;
  font-weight: normal;
}

.post-list {
  list-style: none;
  padding-left: 0;
}

.post-list li {
  margin-bottom: 0.5rem;
  padding: 0.5rem;
  background-color: #f8f9fa;
  border-radius: 4px;
}

.post-meta {
  color: #666;
  font-size: 0.9rem;
  margin-right: 1rem;
}

.post-link {
  color: #1565c0;
  text-decoration: none;
}

.post-link:hover {
  text-decoration: underline;
}
</style>
