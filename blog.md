---
title: "개발 블로그"
permalink: /blog/
layout: single
---

<section class="section-hero">
  <p class="page-chip">Dev Blog</p>
  <h2>HS Finder 개발 이야기</h2>
  <p>앱 개발 과정, 기술 결정, 업데이트 내역을 공유합니다.</p>
</section>

{% assign posts = site.posts | sort: "date" | reverse %}
<div class="post-grid">
{% for post in posts %}
  <article class="post-card">
    <p class="latest-card__meta">
      <span class="category-badge">{{ post.categories | first }}</span>
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
    </p>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p>{{ post.excerpt | strip_html | truncate: 120 }}</p>
  </article>
{% endfor %}
</div>
