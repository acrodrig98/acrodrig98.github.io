---
theme: jekyll-theme-minimal
title: "Blog"
description: Harvard Prize Postdoctoral Fellow | Astrophysicist
permalink: /blog/
---

# Blog

Occasional posts on astrophysics, AI, research, education, and more.

---

{% if site.posts.size > 0 %}
<ul class="post-list">
{% for post in site.posts %}
  <li>
    <a class="post-title" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    <span class="post-meta">{{ post.date | date: "%B %-d, %Y" }}</span>
    <span class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 50 }}</span>
  </li>
{% endfor %}
</ul>
{% else %}
*No posts yet — check back soon.*
{% endif %}
