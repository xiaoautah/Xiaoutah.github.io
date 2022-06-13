---
title: Blog
order: 2
layout: home-page
---


{% assign i = 0 %}
<ol class="post-card-box clearfix">
  {% for post in paginator.posts %}
  <li>
    <div class="post-card">
      {% if post.img %}
      {% assign link = "/assets/img/" | prepend: site.baseurl | append : post.img %}
      {% assign style = "background-image: url(" | append: link | append: ")" %}
      {% else %}
      {% assign color = site.colors[i] %}
      {% unless color %}
        {% assign i = 0 %}
        {% assign color = site.colors[i] %}
      {% endunless %}
      {% assign style = "background: " | append: color %}
      {% assign i = i|plus:1 %}
      {% endif %}
      
      <a href="{{post.url | prepend: site.baseurl}}" class="post-card-image" style="{{style}}">
      </a>

      <div class="post-card-body">
        {% for tag in post.tags %}
        <a href="{{site.baseurl}}/tags#{{tag}}" class="tag">|&#32;{{ tag }}</a>
        {% endfor %}
        <a href="{{post.url | prepend: site.baseurl}}" class="post-card-link"><h3 class="post-card-title">{{post.title}}</h3></a>
      </div>

    </div>
  </li>
  {% endfor %}
</ol>
