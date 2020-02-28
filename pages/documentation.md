---
layout: page
title: Documentation
permalink: '/documentation/'
---

The Digital Beehive was built using [Wax](https://minicomp.github.io/wax/). Annotations are created in a Mirador server, using IIIF images hosted by Stanford University Libraries. The annotations are processed using a Ruby script, producing a master CSV of the data. This CSV is further processed through a series of Python scripts to create the data for the Jekyll site.

For the data sets used to build the site, please visit our [Github](https://github.com/KislakCenter/digital-beehive).

The Ruby code used to process the Mirador annotations can be found in this [repository](https://github.com/upenn-libraries/beehive-scripts).

The scripts used to process the data can be found [here](https://github.com/drnelson6/beehive-scripts). Our raw dataset can be downloaded [here](https://github.com/drnelson6/beehive-scripts/blob/master/data/beehive-data-raw.csv).

You can read more about how we made the Digital Beehive [here](making-the-beehive.md).
