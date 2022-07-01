---
layout: page
title: members
permalink: /members/
description: Group members
nav: true
display_categories: [work, fun]
horizontal: false
---

<!-- pages/members.md -->
<div class="members">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized members -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_members = site.members | where: "category", category -%}
  {%- assign sorted_members = categorized_members | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_members -%}
      {% include members_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_members -%}
      {% include members.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display members without categories -->
  {%- assign sorted_members = site.members | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_members -%}
      {% include members_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_members -%}
      {% include members.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
