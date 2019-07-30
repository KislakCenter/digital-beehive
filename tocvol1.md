---
layout: toc
title: Volume One
description: Navigating Volume One
permalink: '/tocvol1/'
---
<ul class="list-unstyled">
{% for item in site.data.toc_vol1 %}
  <li style="position: relative">
    <hr>
      <a href="{{ item.full }}"><img style="padding: 0 15px; float: left; clear: both; margin-top: 20px; postion: fixed" src="{{ item.thumbnail }}"/></a>
        <div id="text">
          {% if item.pastorius_section_header %}
            {{ item.pastorius_section_header }}<br />
          {% endif %}
          {{ item.section_title }}
          <p style="margin-top: 20px; border-box; position: fixed; height=100%; width=100%"></p>
        </div>
      <br>
  </li>
{% endfor %}
</ul>
