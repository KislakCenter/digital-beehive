---
layout: accordion
title: collapse test
description: collapse test
permalink: '/accordion/'
---

<ul class="list-unstyled">
{% for item in site.data.toc_vol1 %}
  <li style="position: static">
  <div id='divthumbs'>
    <div class= 'divthumb'>
      <hr>
        <a href="{{ site.baseurl }}/toc_vol1/{{ item.pid }}"><img style="padding: 0 15px; float: left; clear: both; margin-top: 20px" src="{{ item.thumbnail }}"/></a>
          {% if item.toc_title %}
            <font color= "teal"><center><h3>{{ item.toc_title }}</h3></center></font>
          {% endif %}
            <!-- {% if item.pastorius_section_header %}
            <font color= "teal"><strong>Pastorius's Title:</strong></font> {{ item.pastorius_section_header }}<br />
            {% endif %} -->
          {% if item.section_title %}
            <strong>Section:</strong> {{ item.section_title }}<br />
          {% endif %}
          {% if item.secondary_section_title %}
            <strong>Section:</strong> {{ item.secondary_section_title }}<br />
          {% endif %}
          {% if item.contents %}
            <strong>Content:</strong> {{ item.contents }}<br />
          {% endif %}
            <i>Volume {{ item.volume }}, Image {{ item.image }}</i>
          <p style="margin-top: 20px; border-box; position: fixed; height=100%; width=100%"></p>
      </div>
    </div>
  </li>
{% endfor %}
</ul>
