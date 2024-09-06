---
layout: page
title: teaching
permalink: /teaching/
description: Materials for courses you taught. Replace this text with your description.
nav: true
nav_order: 4
horizontal: true
---

For now, this page is assumed to be a static description of your courses. You can convert it to a collection similar to `_projects/` so that you can have a dedicated page for each course.

Organize your courses by years, topics, or universities, however you like!

<!-- pages/teaching.md -->
<div class="teaching">

{% assign sorted_teaching = site.teaching | sort: "importance" %}

<!-- Generate cards for each project -->
{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for teaching in sorted_teaching %}
      {% include teaching_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>

{% else %}

  <div class="row row-cols-1 row-cols-md-3">
    {% for teaching in sorted_teaching %}
      {% include teaching.liquid %}
    {% endfor %}
  </div>

{% endif %}

</div>