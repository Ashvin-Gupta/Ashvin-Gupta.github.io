---
layout: book-shelf
permalink: /books/
title: books
description: My book reviews and reading list.
nav: false
nav_order: 9
---

{% for book in site.books %}

<div class="row mt-3">
  <div class="col-sm-2 abbr">
    {% if book.cover %}
      <img src="{{ book.cover | relative_url }}" class="img-fluid rounded z-depth-1" alt="{{ book.title }} cover">
    {% endif %}
  </div>
  <div class="col-sm-10 mt-2 mt-sm-0">
    <div class="title"><a href="{{ book.url | relative_url }}">{{ book.title }}</a></div>
    <div class="author">{{ book.author }}</div>
    <div class="periodical"><em>{{ book.year }}</em></div>
    <div class="links">
      {% if book.url %}
        <a href="{{ book.url | relative_url }}">Review</a>
      {% endif %}
    </div>
    <div class="hidden">{{ book.abstract }}</div>
  </div>
</div>

{% endfor %}
