---
layout: toc
title: Volume One
description: Navigating Volume One
permalink: '/tocvol1/'
---

<div id= 'divsidenav'
  <div class="sidenav">
    <div class="list-group">
      {% for item in site.data.toc_vol1%}
        {% if item.toc_title %}
          <a href="#{{ item.toc_link }}">{{ item.toc_title }}</a><br />
        {% endif %}
      {% endfor %}
    </div>    
  </div>
</div>

<div class="d-inline-flex">
  <p style="margin-left: 315px; margin-right: 15px"> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse tincidunt nunc eu erat lacinia ultrices. Phasellus cursus ullamcorper ornare. Vestibulum eu ante nulla. Nulla ut posuere tellus. Morbi tellus lacus, dictum in pretium eget, elementum non justo. Donec imperdiet vehicula turpis, eget eleifend lacus. Etiam laoreet, metus in rhoncus ornare, mi sapien malesuada metus, accumsan porta ipsum sapien vel arcu. Suspendisse varius orci at consectetur lobortis. Nunc eget neque ultricies, malesuada ligula quis, pellentesque magna. Morbi vestibulum molestie tortor at vestibulum.</p>
</div>


<ul class="list-unstyled">
{% for item in site.data.toc_vol1 %}
  <li style="position: static">
  <div id='divthumbs'>
    <div class= 'divthumb'>
      <hr>
        <a href="{{ site.baseurl }}/toc_vol1/{{ item.pid }}"><img style="padding: 0 15px; float: left; clear: both; margin-top: 10px" src="{{ item.thumbnail }}"/></a>
          <div class="label">
          {% if item.toc_title %}
            <font color= "teal"><h4><a id="{{ item.toc_link }}"></a> {{ item.toc_title }}</h4></font>
          {% endif %}
          <i>Volume {{ item.volume }}, Image {{ item.image }}</i><br />
          {% if item.section_title %}
            <strong>Section:</strong> {{ item.section_title }}<br />
          {% endif %}
          {% if item.secondary_section_title %}
            <strong>Section:</strong> {{ item.secondary_section_title }}<br />
          {% endif %}
          {% if item.contents %}
            <strong>Content:</strong> {{ item.contents }}<br />
          {% endif %}
            <p style="margin-left: 315px; margin-right: 15px; border-box; position: fixed; height=100%; width=100%"></p>
          </div>
    </div>
  </div>
  </li>
{% endfor %}
</ul>
