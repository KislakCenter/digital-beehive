---
layout: default
title: Making the Beehive
description: The blog for the Pastorius Beehive Project
permalink: '/making-the-beehive/'
---

_N.B.: The Beehive Diary is a collection of short essays by members of the Beehive Team on the process of creating the Digital Beehive. These essays gather not only our thoughts on the project, including the technical process of making the Beehive digital and the labor this entails, but also new discoveries we make about the manuscript._ 

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
