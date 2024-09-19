---
layout: page
title: Teaching 
permalink: /teaching/
description: Under construction.
nav: true
nav_order: 4
horizontal: true
display_categories: [Undergraduate course, Graduate course]
---

<!-- For now, this page is assumed to be a static description of your courses. You can convert it to a collection similar to `_projects/` so that you can have a dedicated page for each course. -->

<!-- Organize your courses by years, topics, or universities, however you like! -->

<!-- pages/teaching.md -->
<div class="teaching">

<!-- Display categorized projects -->
  {% for category in page.display_categories %}

  <a id="{{ category }}" href=".#{{ category }}">
    <h4 class="category">{{ category }}</h4>
  </a>

{% assign categorized_teaching = site.teaching | where: "category", category %}
{% assign sorted_teaching = categorized_teaching | sort: "importance" %}

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

{% endfor %}

</div>