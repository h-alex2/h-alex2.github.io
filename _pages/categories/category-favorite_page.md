---
title: "Favorite-Page"
layout: archive
permalink: categories/favoritepage
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories.favoritepage %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
