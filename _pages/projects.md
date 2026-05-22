---
layout: page
title: Projects
permalink: /projects/
description: Selected projects and tools.
nav: false
nav_order: 2
display_categories: []
horizontal: false
---

## Work History

My current work combines graduate study at UC San Diego with business intelligence work at Unified Business Technologies. Recent projects include developer tooling for Azure DevOps workflows, student-retention analytics, and small web systems for organizing shared information.

## Portfolio

### Research / Mathematical Systems

- Quantum decoding infrastructure
- QSVT Hamiltonian simulation
- Sliding-window decoding experiments
- Randomized algorithms
- Computational modeling projects
- Mathematical systems explorations: candidate selection problem.

### Systems / Infrastructure

- Distributed CDN in `Go` using `gRPC`
- Compiler + REPL + VSCode extension
- LLVM / Mobile language ambitions
- Simulation engines
- Sudoku experimentation framework
- Scheduling/iCal tooling

### Architectural / Applied Systems

- AI-assisted intake pipeline
- ADO orcehstration systems
- operation analytics modernization
- data collection infrastructure


- [adoctl](https://github.com/cdylpp/adoctl): Validation and orchestration tooling for AI-assisted planning workflows targeting Azure DevOps infrastructures. Designed around safe automation, schema validation, and operational reliability for agent-generated work decomposition and task management.
- [Student Retention Analytics Tool](https://github.com/cdylpp/srt): Analytics and modeling platform exploring institutional retention dynamics through data pipelines, statistical analysis, and reporting infrastructure. Focused on translating large educational datasets into operationally actionable insights.
- [HomeHub](https://github.com/cdylpp/homehub): Experimental systems design project exploring shared household coordination through unified scheduling, task orchestration, and lightweight workflow management.
- [Personal website](https://github.com/cdylpp/cdylpp.github.io): this Jekyll and GitHub Pages site, rebuilt from a general academic template into a focused professional portfolio.

### Cards

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
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
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

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
