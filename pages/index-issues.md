---
layout: page
title: Issues in the Octavo Index
permalink: /index/issues/
---
This page presents a non-exhaustive list of known issues in the Octavo Index of the Digital Beehive. As issues are discovered, they are added to this list. When an issue is resolved, it is either removed or the issue is modified to reflect the current status of the item.  

{% for item in site.data.index-issues %}
_Volume and image number:_ {{ item.volume }}.{{ item.image_number }} <br>
{{ item.reference_link }} <br>
{{ item.problem }} <br>
<br>
{% endfor %}
