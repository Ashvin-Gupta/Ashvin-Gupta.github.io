---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* Ph.D. in AI for Healthcare, Imperial College London (in progress)
  * AI for Healthcare CDT
  * SPIKE group, supervised by Professor Alessandra Russo

Research interests
======
* Machine learning for electronic health records
* Cancer diagnosis and management
* Computational models of clinical guidelines

Publications
======
<ul>
  {% for post in site.publications reversed %}
    {% include publication-list-item.html %}
  {% endfor %}
</ul>
