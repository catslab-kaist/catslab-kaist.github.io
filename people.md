---
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_array = "pi|postdoc|gradstudent|researchstaff|visiting|others|intern|alumni" | split: "|" %}

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
 {% elsif role == 'intern' %}
<h3>Interns</h3>
 {% elsif role == 'alumni' %}
<h3>Alumni</h3>
{% endif %}
</div>

{% if role != 'alumni' and role != 'intern' %}
<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          {% if profile.avatar %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}" onerror="this.src='{{site.baseurl}}/images/people/404.jpg';" ></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
          {% endif %}
          <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
        </p>
      </div>    
    {% endif %}
  {% endfor %}
</div>
<hr>
{% elsif role == 'intern' %}
<br>
<table>
  <thead>
    <tr>
      <th>Who are they</th>
      <th>When were they here</th>
      <th>Where they went</th>
    </tr>
  </thead>
  <tbody>
    {% for profile in people_sorted %}
      {% if profile.position contains 'intern' %}
        <tr>
          <td><a href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a></td>
          <td>{{ profile.joined }} ~ {{ profile.ended }}</td>
          <td>{{ profile.destination }}</td>
        </tr>
      {% endif %}
    {% endfor %}
  </tbody>
</table>

{% else %}

<br>

<table>
  <thead>
    <tr>
      <th>Who are they</th>
      <th>When were they here</th>
      <th>Where they went</th>
      <th>Graduate thesis/dissertation</th>
    </tr>
  </thead>
  <tbody>
    {% for profile in people_sorted %}
      {% if profile.position contains 'alumni' %}
        <tr>
          <td><a href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a></td>
          <td>{{ profile.joined }} ~ {{ profile.ended }}</td>
          <td>{{ profile.destination }}</td>
          <td>{{ profile.thesis }}</td>
        </tr>
      {% endif %}
    {% endfor %}
  </tbody>
</table>

{% endif %}
{% endfor %}
