---
layout: default
title: Posts
---

<section class="journal-index" aria-labelledby="journal-index-title">
  <h1 id="journal-index-title">{{ page.title | escape }}</h1>

  {% for post in site.posts %}
    {% assign month = post.date | date: "%Y 年 %-m 月" %}
    {% assign month_prefix = month | append: "｜" %}
    {% assign prefix_length = month_prefix | size %}
    {% assign opening = post.title | slice: 0, prefix_length %}
    {% assign entry_title = post.title %}

    {% if opening == month_prefix %}
      {% assign entry_title = post.title | remove_first: month_prefix | strip | default: post.title %}
    {% endif %}

    <article class="journal-entry">
      <time class="journal-stamp" datetime="{{ post.date | date_to_xmlschema }}">
        <span class="journal-year">{{ post.date | date: "%Y" }}</span>
        <span class="journal-month">{{ post.date | date: "%-m" }}<small>月</small></span>
      </time>

      <div class="journal-entry-text">
        <h2>
          <a href="{{ post.url | relative_url }}" aria-label="{{ post.title | escape }}">{{ entry_title | escape }}<span class="journal-arrow" aria-hidden="true">→</span></a>
        </h2>

        {% assign excerpt = post.excerpt | strip_html | strip %}
        {% if excerpt != empty %}
          <p>{{ excerpt | escape_once }}</p>
        {% endif %}
      </div>
    </article>
  {% else %}
    <p>第一篇月誌還在準備中。</p>
  {% endfor %}
</section>
