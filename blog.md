---
layout: default
title: Blog Posts
permalink: /blog
---

<div class="blog-home container-md">
  {%- if page.title -%}
    <h1 class="page-heading">{{ page.title }}</h1>
  {%- endif -%}


  {% if site.paginate %}
    {% assign posts = paginator.posts %}
  {% else %}
    {% assign posts = site.posts %}
  {% endif %}


  {%- if posts.size > 0 -%}
    {%- if page.list_title -%}
      <h1 class="post-list-heading">{{ page.list_title }}</h1>
    {%- endif -%}

    <div class="post-container container-lg">
      <div class="post-row row">
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        {%- for post in posts -%}
          <div class="post-grid col col-md-12 col-sm-12">
            <div class="card">
              <div class="blog-header card-header">
                <h3 class="post-header-title">
                  {{ post.title | escape }}
                </h3>
              </div>
              <div class="card-div card-body">    
                <span class="post-meta">Posted: {{ post.date | date: date_format }}</span>
                <hr>
                {%- if site.show_excerpts -%}
                  {{ post.excerpt }}
                {%- endif -%}

                <a class="read-btn btn btn-primary" href="{{ post.url }}" role="button">Read More</a>
              </div>
            </div>
          </div>
        {%- endfor -%}
      </div>
    </div>

    {% if site.paginate %}
      <div class="pager">
        <ul class="pagination">
        {%- if paginator.previous_page %}
          <li><a href="{{ paginator.previous_page_path | relative_url }}" class="previous-page">{{ paginator.previous_page }}</a></li>
        {%- else %}
          <li><div class="pager-edge">•</div></li>
        {%- endif %}
          <li><div class="current-page">{{ paginator.page }}</div></li>
        {%- if paginator.next_page %}
          <li><a href="{{ paginator.next_page_path | relative_url }}" class="next-page">{{ paginator.next_page }}</a></li>
        {%- else %}
          <li><div class="pager-edge">•</div></li>
        {%- endif %}
        </ul>
      </div>
    {%- endif %}

  {%- endif -%}

</div>
