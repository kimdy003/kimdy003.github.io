---
title: "Basic"
layout: archive
permalink: categories/Basic
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories.Basic %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}