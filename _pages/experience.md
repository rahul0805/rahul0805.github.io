---
layout: page
title: Experience
permalink: /experience/
description: 
nav: true
nav_order: 5
display_categories: [industry, research, other]
# horizontal: false
---

<!-- pages/projects.md -->
<div class="experience">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.experience | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" | reverse %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    {% for project in sorted_projects %}
      <div class="row">
        {% include exp_horizontal.liquid %}
      </div>
    {% endfor %}
  </div>
  {% else %}
    {% for experience in sorted_projects %}
      <div class="row">
        {% include exp.liquid %}
      </div>
    {% endfor %}
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.experience | sort: "importance" | reverse %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    {% for experience in sorted_projects %}
      <div class="row">
        {% include projects_horizontal.liquid %}
      </div>
    {% endfor %}
  </div>
  {% else %}
    {% for project in sorted_projects %}
      <div class="row">
        {% include projects.liquid %}
      </div>
    {% endfor %}
  {% endif %}
{% endif %}
</div>