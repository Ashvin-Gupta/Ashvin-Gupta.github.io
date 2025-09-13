---
layout: default
permalink: /blog/
title: blog
nav: true
nav_order: 1
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1 # The number of links before the current page
    after: 3 # The number of links after the current page
---

<div class="post">
  <header class="post-header">
    <h1 class="post-title">{{ page.title }}</h1>
    <p class="post-description">{{ page.description }}</p>
  </header>

  <article>
    {% if site.blog_nav %}
      <div class="blog-nav">
        <div class="row">
          <div class="col-md-12">
            <div class="btn-group" role="group" aria-label="Blog navigation">
              <a href="{{ '/blog/' | relative_url }}" class="btn btn-outline-primary {% if paginator.page == 1 %}active{% endif %}">All Posts</a>
              {% assign sorted_categories = site.categories | sort %}
              {% for category in sorted_categories %}
                <a href="{{ category[0] | slugify | prepend: '/blog/category/' | relative_url }}" class="btn btn-outline-primary">{{ category[0] | capitalize }}</a>
              {% endfor %}
            </div>
          </div>
        </div>
      </div>
    {% endif %}

    {% if site.display_tags or site.display_categories %}
      <div class="tag-category-list">
        <div class="row mt-3">
          <div class="col-md-12">
            {% if site.display_categories %}
              {% assign categories = "" | split: "" %}
              {% for post in site.posts %}
                {% assign categories = categories | concat: post.categories %}
              {% endfor %}
              {% assign categories = categories | uniq | sort %}
              {% if categories.size > 0 %}
                <h6>Categories:</h6>
                {% for category in categories %}
                  <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}" class="badge badge-light text-uppercase align-middle" style="font-size: 12px;">{{ category }}</a>
                {% endfor %}
              {% endif %}
            {% endif %}
            {% if site.display_tags %}
              {% assign tags = "" | split: "" %}
              {% for post in site.posts %}
                {% assign tags = tags | concat: post.tags %}
              {% endfor %}
              {% assign tags = tags | uniq | sort %}
              {% if tags.size > 0 %}
                <h6 class="mt-2">Tags:</h6>
                {% for tag in tags %}
                  <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}" class="badge badge-light text-uppercase align-middle" style="font-size: 12px;">{{ tag }}</a>
                {% endfor %}
              {% endif %}
            {% endif %}
          </div>
        </div>
      </div>
    {% endif %}

    {% assign blog_name_size = site.blog_name | size %}
    {% assign blog_description_size = site.blog_description | size %}

    {% if blog_name_size > 0 or blog_description_size > 0 %}
      <div class="header-bar">
        <h1>{{ site.blog_name }}</h1>
        <h2>{{ site.blog_description }}</h2>
      </div>
    {% endif %}

    {% if site.display_tags or site.display_categories %}
      {% include blog_tags.liquid %}
    {% endif %}

    {% assign featured_posts = site.posts | where: "featured", "true" %}
    {% if featured_posts.size > 0 %}
      <br />
      <div class="container featured-posts">
        <div class="row">
          <div class="col-md-12">
            <h2>Featured Posts</h2>
            <hr />
          </div>
        </div>
        <div class="row">
          {% for post in featured_posts %}
            <div class="col-md-12">
              <div class="card-item">
                {% if post.redirect == blank %}
                  <a href="{{ post.url | relative_url }}">
                {% else %}
                  {% if post.redirect contains '://' %}
                    <a href="{{ post.redirect }}" target="_blank">
                  {% else %}
                    <a href="{{ post.redirect | relative_url }}">
                  {% endif %}
                {% endif %}
                  <div class="card hoverable">
                    <div class="row g-0">
                      <div class="col-md-12">
                        <div class="card-body">
                          <div class="float-right">
                            <i class="fa-solid fa-thumbtack fa-xs"></i>
                          </div>
                          <h3 class="card-title text-lowercase">{{ post.title }}</h3>
                          <p class="card-text">{{ post.description }}</p>

                          {% if post.external_source == blank %}
                            {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
                          {% else %}
                            {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
                          {% endif %}
                          {% assign year = post.date | date: "%Y" %}

                          <p class="post-meta">
                            {{ read_time }} min read &nbsp; &middot; &nbsp;
                            <a href="{{ year | prepend: '/blog/' | relative_url }}">
                              <i class="fa-solid fa-calendar fa-sm"></i> {{ year }}
                            </a>
                            {%- if post.external_source %}
                              &nbsp; &middot; &nbsp; {{ post.external_source }}
                            {%- endif %}
                          </p>
                          <p class="post-tags">
                            {% if post.tags != blank %}
                              &nbsp; &middot; &nbsp;
                              {% for tag in post.tags %}
                                <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">
                                  <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag }}
                                </a>
                                {% unless forloop.last %}
                                  &nbsp;
                                {% endunless %}
                              {% endfor %}
                            {% endif %}
                          </p>
                        </div>
                      </div>
                    </div>
                  </div>
                </a>
              </div>
            </div>
          {% endfor %}
        </div>
      </div>
      <hr />
    {% endif %}

    <ul class="post-list">
      {% if page.pagination.enabled %}
        {% assign postlist = paginator.posts %}
      {% else %}
        {% assign postlist = site.posts %}
      {% endif %}

      {% for post in postlist %}
        {% if post.external_source == blank %}
          {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
        {% else %}
          {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
        {% endif %}
        {% assign year = post.date | date: "%Y" %}
        {% assign tags = post.tags | join: "" %}
        {% assign categories = post.categories | join: "" %}

        <li>
          <div class="row">
            <div class="col-sm-9">
              {% if post.redirect == blank %}
                <h3><a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
              {% else %}
                <h3><a class="post-title" href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
                  <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
                    <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
                  </svg>
                </h3>
              {% endif %}
              <p>{{ post.description }}</p>
            </div>
            <div class="col-sm-3">
              <p class="post-meta">
                {{ read_time }} min read &nbsp; &middot; &nbsp;
                <a href="{{ year | prepend: '/blog/' | relative_url }}">
                  <i class="fa-solid fa-calendar fa-sm"></i> {{ year }}
                </a>
                {%- if post.external_source %}
                  &nbsp; &middot; &nbsp; {{ post.external_source }}
                {%- endif %}
              </p>
              <p class="post-tags">
                {% if tags != "" %}
                  {% for tag in post.tags %}
                    <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">
                      <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag }}
                    </a>
                    {% unless forloop.last %}
                      &nbsp;
                    {% endunless %}
                  {% endfor %}
                {% endif %}
              </p>
            </div>
          </div>
        </li>
      {% endfor %}
    </ul>

    {% if page.pagination.enabled %}
      {% include pagination.liquid %}
    {% endif %}
  </article>
</div>
