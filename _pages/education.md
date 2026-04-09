---
layout: page
title: Education
permalink: /education/
description: 研究指導・教育
nav: true
nav_order: 4
---

### Courses

[担当授業はこちら](https://www.tus.ac.jp/ridai/doc/ji/RIJIA01Detail.php?act=&kin=jug&diu=3981){:target="_blank"}

---

### For students
安井研究室では、ものづくり、サービスの研究や統計解析に興味がある方を歓迎しています。

{% assign sorted_education = site.education | sort: "importance" %}
<div class="row row-cols-1 row-cols-md-3 g-2">
  {% for education in sorted_education %}
    {% include education.liquid %}
  {% endfor %}
</div>


