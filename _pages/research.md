---
layout: page
title: Research
permalink: /research/
description: Our research topics and supported grants.
nav: true
nav_order: 2
display_categories: [work, fun]
horizontal: true
---


---
### Our research scope

**Mathematical Imaging Processing**
We focus on developing advanced mathematical techniques to improve image quality and analysis. This involves creating algorithms for noise reduction, image enhancement, and feature extraction, which are crucial for various applications in science and technology.

**Medical Imaging Processing**
Our work in medical imaging aims to enhance diagnostic accuracy and patient outcomes. We utilize state-of-the-art technologies to process and analyze medical images such as CT, MRI, and X-rays, striving to develop tools that assist healthcare professionals in early detection and treatment planning.

**Machine Learning**
We apply machine learning to solve complex problems across a range of disciplines. Our research includes developing algorithms for pattern recognition, predictive modeling, and data mining, which are integral to advancements in artificial intelligence and automation.

**Optimization**
Our optimization research focuses on finding the most efficient solutions to complex problems. This includes optimizing algorithms for speed and accuracy in computational tasks, as well as addressing real-world challenges in engineering, logistics, and resource management.

---
### Grants (to be update)

<!-- pages/research.md -->
<div class="project">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.research | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include research_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include research.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.research | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include research_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include research.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

