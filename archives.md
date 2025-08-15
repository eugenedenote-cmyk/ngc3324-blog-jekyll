---
layout: page
title: 아카이브
permalink: /archives/
---

<div class="archive-list">
  {% assign posts_by_year = site.posts | group_by_exp: 'post', 'post.date | date: "%Y"' %}
  {% for year_posts in posts_by_year %}
    <div class="year-group">
      <h2 class="year-title">{{ year_posts.name }}년</h2>
      
      {% assign posts_by_month = year_posts.items | group_by_exp: 'post', 'post.date | date: "%m"' %}
      {% for month_posts in posts_by_month %}
        <div class="month-group">
          <h3 class="month-title">{{ month_posts.name | plus: 0 }}월</h3>
          <ul class="post-list">
            {% for post in month_posts.items %}
              <li class="archive-post">
                <span class="post-date">{{ post.date | date: "%d일" }}</span>
                <a href="{{ post.url | relative_url }}" class="post-title">{{ post.title }}</a>
                {% if post.categories.size > 0 %}
                  <span class="post-category">[{{ post.categories | first }}]</span>
                {% endif %}
              </li>
            {% endfor %}
          </ul>
        </div>
      {% endfor %}
    </div>
  {% endfor %}
</div>

<style>
.archive-list {
  margin: 2rem 0;
}

.year-group {
  margin-bottom: 3rem;
}

.year-title {
  color: #1565c0;
  border-bottom: 2px solid #1565c0;
  padding-bottom: 0.5rem;
  margin-bottom: 1.5rem;
}

.month-group {
  margin-bottom: 2rem;
  margin-left: 1rem;
}

.month-title {
  color: #424242;
  font-size: 1.2rem;
  margin-bottom: 1rem;
}

.post-list {
  list-style: none;
  padding-left: 0;
}

.archive-post {
  margin-bottom: 0.8rem;
  padding: 0.8rem;
  background-color: #f8f9fa;
  border-radius: 6px;
  border-left: 4px solid #e3f2fd;
  transition: all 0.2s ease;
}

.archive-post:hover {
  background-color: #e3f2fd;
  border-left-color: #1565c0;
}

.post-date {
  color: #666;
  font-size: 0.9rem;
  font-weight: 500;
  margin-right: 1rem;
  min-width: 3rem;
  display: inline-block;
}

.post-title {
  color: #1565c0;
  text-decoration: none;
  font-weight: 500;
}

.post-title:hover {
  text-decoration: underline;
}

.post-category {
  color: #666;
  font-size: 0.8rem;
  margin-left: 0.5rem;
  background-color: #e0e0e0;
  padding: 0.2rem 0.5rem;
  border-radius: 3px;
}
</style>
