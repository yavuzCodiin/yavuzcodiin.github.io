---
layout: page
title: Sketches
permalink: /sketches/
---

<div class="sketches-grid">
  {% for sketch in site.sketches %}
    <div class="sketch">
      <img src="{{ sketch.image | prepend: site.baseurl }}" alt="Sketch image">
    </div>
  {% endfor %}
</div>