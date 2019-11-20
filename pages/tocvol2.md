---
layout: toc
title: Volume Two
description: Navigating Volume Two
permalink: '/tocvol2/'
---

<div id= 'divsidenav'
  <div class="sidenav">
    <div class="list-group">
      <p style="letter-spacing: 0.04em; list-style-type: circle"><font color= "black"><h3>Navigation</h3></font></p>
      {% for item in site.data.master_toc%}
      {% case item.volume %}
        {% when '2' %}
          {% if item.toc_title %}
            <a href="#{{ item.toc_link }}">{{ item.toc_title }}</a><br />
          {% endif %}
      {% endcase %}
      {% endfor %}
    </div>    
  </div>
</div>

<div class="d-inline-flex">
  <p style="margin-left: 315px; margin-right: 15px">This section provides a page-by-page overview of the second volume of the Beehive as it is currently bound. You can find an explanation of this division and a user guide for page browsing <a href="{{ site.baseurl }}/pagebrowse/">here</a>. The navigation is divided largely by divisions that we've created for ease of use, and it is otherwise divided and represented by Pastorius's own language. Additionally, each of these divisions is marked by its volume and image number for locational reference. <br />
  <br />This volume provides the browsable content for the linked <a href="{{ site.baseurl }}/alphabetical/)">Alphabetical Section</a> and <a href="{{ site.baseurl }}/numerical/)">Numerical Section</a> entries.</p>
</div>


<ul class="list-unstyled">
{% for item in site.data.master_toc %}
{% case item.volume %}
  {% when '2' %}
  <li style="position: static">
  <div id='divthumbs'>
    <div class= 'divthumb'>
      <hr>
        <a href="{{ site.baseurl }}/toc/{{ item.pid }}"><img style="padding: 0 15px; float: left; clear: both; margin-top: 10px" src="{{ item.thumbnail }}"/></a>
          <div class="label">
          {% if item.toc_title %}
            <font color= "#a47b02"><h4><a id="{{ item.toc_link }}"></a> {{ item.toc_title }}</h4></font>
          {% endif %}
          <i>Volume {{ item.volume }}, Image {{ item.image }}</i><br />
          {% if item.tertiary_section_title %}
            <strong>Section:</strong> {{ item.section_title }} | {{ item.secondary_section_title }} | {{ item. tertiary_section_title }}<br />
          {% elsif item.secondary_section_title %}
              <strong>Section:</strong> {{ item.section_title }} | {{ item.secondary_section_title }}<br />
          {% elsif item.section_title %}
            <strong>Section:</strong> {{ item.section_title }}<br />
          {% endif %}
          {% if item.contents %}
            <strong>Content:</strong> {{ item.contents }}<br />
          {% endif %}
          {% if item.first_entry %}
            <strong>Range:</strong> {{ item.first_entry }}
          {% endif %}
          {% if item.last_entry %}
            - {{ item.last_entry }} <br>
          {% endif %}
          </div>
    </div>
  </div>
  </li>
{% endcase %}
{% endfor %}
</ul>

<script src="https://unpkg.com/vanilla-back-to-top@7.2.1/dist/vanilla-back-to-top.min.js"></script>
<script>addBackToTop({
  diameter: 56,
  backgroundColor: 'rgb(173, 135, 31)',
  textColor: '#fff'
})</script>
