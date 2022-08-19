---
title: "CS지식"
layout: arhive
permalink: categories/cs
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Cs}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}