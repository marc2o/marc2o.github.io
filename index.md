---
layout: index
title: Hello, I’m Marc!
author: marc2o
language: en-US
image: /images/marc2o-r66.jpg
---

# Hey!

[I’m Marc]({% link about.md %}), somewhat creative and I love making stuff.

I’m into retro gaming and computing, books and writing, drawing with pixels and vectors, coding in Lua and C, and making music with synths and ukulele.

[Some of the stuff I am making.]({% link stuff.md %})

<figure class="grid">
  <img src="/images/icons/textmate.png" alt="TextMate app icon">
  <img src="/images/icons/zettlr.png" alt="Zettlr app icon">
  <img src="/images/pixelart/the-son-of-man.png" alt="The Son of Man pixel art">
  <img src="/images/gamedev-love.png" alt="Game screenshot">
  <img src="/images/pixelart/david.png" alt="David pixel art">
  <img src="/images/icons/naroth.png" alt="Naroth game icon">
  <img src="/images/pixelart/karl.png" alt="Karl Lagerfeld pixel art">
  <img src="/images/cessare.png" alt="Cessare game screenshot">
  <img src="/images/bandcamp.nano.jpg" alt="Music cover">
  <img src="/images/gamedev-c.png" alt="Game screenshot">
  <img src="/images/logo-example.jpg" alt="Logo Project">
</figure>

## Tech Blog (German)

This blog is about retro gaming and computing stuff, experiences and documentations.

{% include posts.html %}

## Code Repositories

<figure class="grid">
{% for repository in site.github.public_repositories %}
{% unless repository.name contains "marc2o" or repository.name contains "Icon" %}
<div class="repo">
  <h4><a href="{{repository.html_url}}" target="_blank">{{repository.name}}</a></h4>
  <p>{{repository.description}}</p>
  {% if repository.language  and repository.language != "" and repository.language ≠ nil %}<label><span class="code_language GitHub_{{repository.language}}"></span><span>{{repository.language}}</span></label>{% endif %}
</div>
{% endunless %}
{% endfor %}
</figure>

<!--
{% if site.data.items and site.data.items.size != 0 %}
<figure>
{% for item in site.data.items %}
<figure><img src="{{ item.img }}" alt="{{ item.name }}">
<figcaption>{{ item.name }}</figcaption></figure>
{% endfor %}
</figure>
{% endif %}
-->