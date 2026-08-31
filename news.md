---
title: News
permalink: /news/
---

### News

<div class="content list">
  {% assign all_news = site.data.news | sort: 'date' | reverse %}
  <ul style="list-style-position:outside;padding:20px">
    {% for new in all_news %}
      <li style="margin-bottom: 1.5em;">
        <small>{{ new.date | date: "%B %Y" }}</small><br>
        {{ new.details }}
      </li>
    {% endfor %}
  </ul>
</div>
