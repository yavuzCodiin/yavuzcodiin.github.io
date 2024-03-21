---
layout: page
title: Thoughts
permalink: /thoughts/
---

<section>
  {% assign sorted_thoughts = site.thoughts | sort: 'date' | reverse %}
  {% if sorted_thoughts.size > 0 %}
    {% for thought in sorted_thoughts %}
      <article class="thought">
        <p>{{ thought.content | strip_html | truncatewords: 1500 }}</p>
        <div class="thought-date">{{ thought.date | date: "%d %b %Y" }}</div>
      </article>
    {% endfor %}
  {% endif %}
</section>
