---
title: "PROJECTS"
layout: archive
permalink: categories/projects
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories.projects %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
