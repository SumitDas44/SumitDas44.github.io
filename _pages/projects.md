
---
layout: page
title: projects
permalink: /projects/
description: "Explore my research and technical projects in wireless sensor networks, machine learning, computer vision, robotics, IoT, networking, and electronics."
nav: true
nav_order: 3
display_categories: [research, robotics-computer-vision, computer-networks, internet-of-things, electronics-simulation, web-database]
horizontal: false
---

<!-- pages/projects.md -->

<div class="projects">

{% if site.enable_project_categories and page.display_categories %}

  <!-- Display categorized projects -->
  {% for category in page.display_categories %}

    {% assign categorized_projects = site.projects | where: "category", category %}
    {% assign sorted_projects = categorized_projects | sort: "importance" %}

    {% if sorted_projects.size > 0 %}

      {% assign category_title = category | replace: "-", " " | capitalize %}

      {% case category %}
        {% when "research" %}
          {% assign category_title = "Research Projects" %}
        {% when "robotics-computer-vision" %}
          {% assign category_title = "Robotics & Computer Vision" %}
        {% when "computer-networks" %}
          {% assign category_title = "Computer Networks" %}
        {% when "internet-of-things" %}
          {% assign category_title = "Internet of Things (IoT)" %}
        {% when "electronics-simulation" %}
          {% assign category_title = "Electronics & Simulation" %}
        {% when "web-database" %}
          {% assign category_title = "Web Development & Database" %}
      {% endcase %}

      <a id="{{ category }}" href="#{{ category }}">
        <h2 class="category">{{ category_title }}</h2>
      </a>

      <!-- Generate project cards -->
      {% if page.horizontal %}

        <div class="container">
          <div class="row row-cols-1 row-cols-md-2">
            {% for project in sorted_projects %}
              {% include projects_horizontal.liquid %}
            {% endfor %}
          </div>
        </div>

      {% else %}

        <div class="row row-cols-1 row-cols-md-3">
          {% for project in sorted_projects %}
            {% include projects.liquid %}
          {% endfor %}
        </div>

      {% endif %}

    {% endif %}

  {% endfor %}

{% else %}

  <!-- Display projects without categories -->
  {% assign sorted_projects = site.projects | sort: "importance" %}

  {% if page.horizontal %}

    <div class="container">
      <div class="row row-cols-1 row-cols-md-2">
        {% for project in sorted_projects %}
          {% include projects_horizontal.liquid %}
        {% endfor %}
      </div>
    </div>

  {% else %}

    <div class="row row-cols-1 row-cols-md-3">
      {% for project in sorted_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>

  {% endif %}

{% endif %}

</div>
