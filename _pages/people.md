---
layout: page
permalink: /people/
title: people
description: members of the group
nav: true
nav_order: 1
display_categories: [faculty, postdoc, phd student, master student, undergraduate, alumni]
---


<!-- pages/people.md -->
<div class="people">

  <!-- Display categorized projects -->
  {% for category in page.display_categories %}

  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
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

