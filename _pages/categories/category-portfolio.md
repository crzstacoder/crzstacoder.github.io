---
title: "Develop Portfolio"
layout: archive
permalink: /portfolio
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories.portfolio %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
