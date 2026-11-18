{% for post in site.posts %}
<article>
  <p class="post-meta">{{ post.date | date: "%Y/%m/%d" }}</p>
  <h2><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h2>
  {{ post.excerpt }}
  <p><a href="{{ post.url | relative_url }}">閱讀全文 →</a></p>
</article>
{% unless forloop.last %}
<hr>
{% endunless %}
{% endfor %}
