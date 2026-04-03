---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

<!-- Replace the content below with your own CV -->

Education
======
* B.S. in Your Major, Your University, 20XX

Work Experience
======
* 20XX - Present: Your Role
  * Company/Organization
  * Description of your work

Skills
======
* Skill Category 1
  * Sub-skill 1.1
  * Sub-skill 1.2
* Skill Category 2

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
