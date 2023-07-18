---
layout: page
title: About Our Data
permalink: '/data/'
---

#### Our Data
We share our data on our [GitHub](https://github.com/KislakCenter/digital-beehive/). 
#### Building the Digital Beehive
In addition to the metadata categories described on the [Data Model page](https://kislakcenter.github.io/digital-beehive/data-structure/), the following categories are generated while building the site:
- pid: persistent identifier for each annotation, used for paths and correct ordering on the website.
- volume: the volume from the Beehive the annotation is in (e.g. 1, 2, or 3).
- image_number: the image number from a specific volume from the Beehive the annotation is on.
- first_letter: the first letter of the alphabetical entry or index header, or the numerical range of the numerical entry (e.g. 51-100), used for facet browsing.
- unparsed: elements of the annotation not parsed automatically, used in data clean-up and review.
<br> 

#### Sorts and Corrections
In addition to the core data, the following additional data sets are used in building the site:

- [Alphabetical Sorts](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/beehive-alpha-sorts.csv)
- [Index Sorts](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/beehive-index-sorts.csv)

These files provide the "first_letter" metadata used to build the website for alphabetical and index entries, in the case that the entry or head field does not begin with the expected letter (e.g. "False Comfort" is ordered under "C", not "F."")

#### Building Cross-references

- [Alphabetical Corrections](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/alpha-corrections.csv)
- [Index Add Corrections](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/index-add-corrections.csv)
- [Index See Corrections](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/index-see-corrections.csv)

These files are used to build cross-references on the website. Because the project follows Pastorius’s orthography exactly, only some data will match automatically. In the case that Pastorius cross-references to an entry using a different version of the word than the corresponding entry (e.g. xref “punishmt” should link to entry "Punishment"), the cross-reference and its intended target are recorded here.

#### Corrections and Issue notes
- [Alphabetical Corrections](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/alpha-corrections.csv)
- [Index Add Corrections](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/index-add-corrections.csv)
- [Index See Corrections](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/index-see-corrections.csv)

These files are used to document uncertainties and editorial decisions made while annotating the Beehive and building the site. In the event an annotation has an issue, the issue will appear on its corresponding page.

#### Building Page references
- [Pastorius pages](https://github.com/KislakCenter/beehive-annotation-scripts/blob/master/data/pastorius-pages.csv)

This file is used to build the page references. It supplies a list of page references in the Beehive along with their corresponding pid from the Table of Contents. Note that it differs from the page numbers supplied in the Table of Contents in that the fields “pastorius_page_numbers” and “older_pastorius_page_numbers” have been collapsed into one.