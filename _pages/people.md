---
layout: page
permalink: /people/
title: Group
description: Members of the group.
nav: true
nav_order: 2
display_categories: [Faculty, Post-doc, PhD student, Master student, Undergraduate, Alumni]
---


<!-- pages/people.md -->
<div class="people">

  <!-- Display categorized projects -->
  {% for category in page.display_categories %}  

  <a id="{{ category }}" href=".#{{ category }}">
    <h4 class="category">{{ category }}</h4>
  </a>

  {% assign categorized_people = site.people | where: "category", category %}
  {% assign sorted_people = categorized_people | sort: "importance" %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for people in sorted_people %}
      {% include people.liquid %}
    {% endfor %}
    </div>
  </div>

  {% endfor %}


</div>

