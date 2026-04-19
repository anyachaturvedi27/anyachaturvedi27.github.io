---
layout: default
title: news
permalink: /news/
description: Updates on publications, talks, awards, and academic activities.
nav: true
nav_order: 5
---
<div class="post">
  <header class="post-header">
    <h1 class="post-title">news</h1>
    {% if page.description %}
        <p class="page-description">{{ page.description }}</p>
    {% endif %}
  </header>

  <article>
    {% assign all_news = site.news | sort: "date" | reverse %}
    <div class="table-responsive">
      <table class="table table-sm table-borderless">
        {% for item in all_news %}
          <tr>
            <th scope="row" style="width: 20%">{{ item.date | date: '%b %d, %Y' }}</th>
            <td>
              {% if item.inline %}
                {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
              {% else %}
                <a class="news-title" href="{{ item.url | relative_url }}">{{ item.title }}</a>
              {% endif %}
            </td>
          </tr>
        {% endfor %}
      </table>
    </div>
  </article>
</div>
