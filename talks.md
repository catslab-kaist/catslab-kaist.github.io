---
title: Talks
permalink: /talks/
---

### Talks & Materials
Slides and materials from talks given by lab members outside the lab — invited talks, conference presentations, and more.

<div class="content list">
  {% for post in site.posts %}
    <div class="list-item">
      <p class="list-post-title">
        <a href="{{ site.baseurl }}{{ post.url }}">- {{ post.title }}</a> (<small>{{post.date | date: "%m/%d/%y" }}</small>)
      </p>
    </div>
  {% endfor %}
</div>
