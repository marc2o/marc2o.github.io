---
layout: article
title: I like to make stuff
author: marc2o
language: en-US
image: /images/marc2o-r66.jpg
---

There is not much to say, I think, other than I –

- am left-handed and
- an astronomer rather than an astronaut;
- like fall (or autumn)
- am a child of the 1980’s home computer revolution
- love books and reading
- love to play on my Ortega Concert Ukulele my AKAI Pro MPK mini Play MK3
- like most to code in Lua, JavaScript and, recently, in C
- also enjoyed BASIC, 68K Assembly, Forth, Java, C# and Rust at some point
- can have fun with HTML & CSS
- _(to be continued, possibly)_


## Some code projects on GitHub

{% for repository in site.github.public_repositories %}
{% unless repository.name contains "marc2o" %}
- **[{{repository.name}}]({{repository.html_url}})**<br>_{{repository.description}}_ {% if repository.language  and repository.language != "" and repository.language ≠ nil %}<br><span class="code_language GitHub_{{repository.language}}"></span><span>{{repository.language}}</span>{% endif %}
{% endunless %}
{% endfor %}

<!-- <figure>
    <span><iframe frameborder="0" src="https://itch.io/embed-upload/270605?color=101010" allowfullscreen="" width="100%" height="660"><a href="https://marc2o.itch.io/cessare">Play Cessare on itch.io</a></iframe></span>
    <figcaption><a href="https://marc2o.itch.io/cessare" target="_blank">Cessare</a></figcaption>
</figure> -->
