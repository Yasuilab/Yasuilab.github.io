---
layout: page
title: Education
permalink: /education/
description: 研究指導・教育
nav: true
nav_order: 4
---

## 求める学生像

wip

{% assign sorted_education = site.education | sort: "importance" %}
<div class="row row-cols-1 row-cols-md-3 g-2">
  {% for education in sorted_education %}
    {% include education.liquid %}
  {% endfor %}
</div>
