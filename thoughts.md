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
        <div class="thought-content">{{ thought.content | newline_to_br }}</div>
        <div class="thought-date">{{ thought.date | date: "%d/%m/%Y" }}</div>
      </article>
    {% endfor %}
  {% endif %}
</section>