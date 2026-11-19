---
layout: default
title: Posts
---

{% for post in site.posts %}
<article>
  <p class="post-meta">{{ post.date | date: "%Y/%m/%d" }}</p>

  <h2>
    <a href="{{ post.url | relative_url }}" style="color: inherit;">{{ post.title | escape }}</a>
  </h2>

  {{ post.excerpt }}

  <p>
    <a href="{{ post.url | relative_url }}"
       aria-label="閱讀全文：{{ post.title | escape }}"
       style="color: #625e58; text-decoration: underline; text-underline-offset: 3px;">閱讀全文 →</a>
  </p>
</article>
{% unless forloop.last %}
<hr>
{% endunless %}
{% endfor %}
