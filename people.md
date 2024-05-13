---
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_array = "pi|postdoc|gradstudent|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if role == 'postdoc' %}
<h3>Postdoctoral Fellows</h3>
 {% elsif role == 'pi' %}
<h3>Principal Investigator</h3>
 {% elsif role == 'gradstudent' %}
<h3>Graduate Students</h3>
 {% elsif role == 'researchstaff' %}
<h3>Research Staff</h3>
 {% elsif role == 'visiting' %}
<h3>Visiting Scholars</h3>
 {% elsif role == 'others' %}
<h3>Honorary Members</h3>
 {% elsif role == 'alumni' %}
<h3>Alumni</h3>
{% endif %}
</div>

{% if role != 'alumni' %}
<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          {% if profile.avatar %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
          {% endif %}
          <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
        </p>
      </div>    
    {% endif %}
  {% endfor %}
</div>

[Gilbert Yang Ye](http://gilbert-yangye.github.io/) joined **Northeastern University** as an **Assistant Professor** in the Department of Civil and Environmental Engineering in January 2025. 
He is a researcher and engineer in the field of human-robot interaction and robotics for resilient infrastructures in civil engineering. 
He obtained my Ph.D. from the Department of Civil & Coastal Engineering at the University of Florida under the supervision of Dr. [Eric Jing Du](https://faculty.eng.ufl.edu/ericdu/). 
His research focuses on automation and workforce engagement in civil engineering with advanced robotics, 
human-centric artificial intelligence, and human-robot interaction methods inspired by human sensorimotor processes. 
He  has published over 20 papers on top conferences and journals. He also serves as a reviewer in multiple journals such as Journal of Construction Engineering and Management, 
Advanced Engineering Informatics, Computers in Human Behavior, International Journal of Human-Computer Interaction, and conferences. He is a member of ASCE, IEEE, and HFES.
<hr>

{% else %}

<br>

| Who are they | When were they here | Where they went |
| :------------- |:-------------| :-----------|
| [xxx](https://www.xxx.com/) | Graduate Student (20xx-20xx) | PhD Student,XXX |

{% endif %}
{% endfor %}
