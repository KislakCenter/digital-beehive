---
layout: page
title: Documentation
permalink: '/documentation/'
---

Annotations for this project were created on a Mirador 
[SimpleAnnotationServer](https://github.com/glenrobson/SimpleAnnotationServer), 
using [IIIF](https://iiif.io) images hosted by Stanford 
University Libraries. We use a Ruby script to produce 
a master CSV of the annotations entered on the server. 
The Ruby code can be found [here](https://github.com/upenn-libraries/beehive-scripts).

This CSV is further processed through a series of Python 
scripts that sort and parse the data in the CSV and produce
output CSVs used to build the website. The Python scripts 
can be found [here](https://github.com/KislakCenter/beehive-annotation-scripts). 
The CSVs used to build the website can be found in this 
Github repoistory in the [data](https://github.com/KislakCenter/beehive-annotation-scripts/tree/master/data) 
folder. 

The Digital Beehive website was built using [Jekyll](https://jekyllrb.com/),
a static site generator along with [Wax](https://minicomp.github.io/wax/),
an extensible workflow developed for creating scholarly 
exhibitions with minimal effort. To view the files used 
to build the site, please visit our [Github](https://github.com/KislakCenter/digital-beehive).

Our datasets can be downloaded [here](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/beehive-data-raw.csv).

You can read more about how we made the Digital Beehive [here]
(making-the-beehive.md).
