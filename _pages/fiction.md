---
title: "Fiction"
layout: splash
permalink: /fiction/
---

<br>

# Creative Writing

## Short Stories
{% for story in site.fiction_writings %}
  <p>
    <a href="{{ story.url }}" style="font-size: 25px">
      <strong> {{ story.title }} </strong>
    </a>
  </p>
{% endfor %}
