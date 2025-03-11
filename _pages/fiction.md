---
title: "fiction"
layout: default
permalink: /fiction/
---
# Short Stories

{% for story in site.fiction_writings %}
  <p>
    <a href="{{ story.url }}" style="font-size: 20px">
      <strong> {{ story.title }} </strong>
    </a>
  </p>
{% endfor %}