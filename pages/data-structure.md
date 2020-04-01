---
layout: page
title: Beehive Data Structure
permalink: '/data-structure/'
---

The Digital Beehive Project uses a Mirador annotation server to create the linked entries of the Beehive. Each annotation is linked to a canvas, which is defined as a page from the Beehive.

The core data for the Digital Beehive Project consists of the annotations and canvases created in the Mirador server. These annotations provide minimal metadata that copies, as exactly as possible, the material of the Beehive.

A typical annotation from the Alphabetical Section looks like this:

![Nature](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0502/337,2763,3008,507/full/0/default.jpg)

```
Entry: Nature
Topic: Nature
Xref: Poverty
Xref: Custom
Xref: 1663 [Nature]
Index: nature
#item-ced0ebdf8
```

- For alphabetical entries, "Entry" and "Topic" are identical. They refer to the underlined title for the entry.
- "Xref" denotes all cross-references. Cross-references occur either directly to the right of the underlined topic, or at the end of the entry, and are indicated through the word "Add." If Pastorius writes just a word, it is assumed this refers to another alphabetical entry and is entered exactly as Pastorius notates it. If he writes a number, it is assumed this refers to a numerical entry. The number is provided along with the topic for the corresponding entry.
- "Index" refers to the corresponding index entry and matches the "Head" field for the corresponding item in the index.
- The item tag is randomly generated and is used in building the site. Item tags do not appear on the Digital Beehive web interface but can be found in our [datasets](https://kislakcenter.github.io/digital-beehive/).

A typical annotation from the Numerical Section looks like this:

![Laconism](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0535/824,774,2946,448/full/0/default.jpg)

```
Entry: 2
Topic: Laconism
Xref: Brevity
Xref: 1169 [Laconism]
Index: few words
Index: Lacedemonians & Laconism
Index: little talk
item-eb4bf567f
```

- For numerical entries, "Entry" refers to the number assigned to the entry, and "Topic" refers to the underlined descriptive title for the entry.
- "Xref" denotes all cross-references, as in the Alphabetical Section.
- "Index" refers to the corresponding index entries, as in the Alphabetical Section. Note that entries may be referenced multiple times in the index, or not at all.
- The item tag works like in the Alphabetical Section.

A typical annotation from the Index looks like this:

![bible](https://stacks.stanford.edu/image/iiif/gw497tq8651%2F1607_0953/1090,234,517,134/full/0/default.jpg)

```
Head: bible
Entry: a
Entry: 421 [Bible]
Page: p.41 [Image 1.101]
#item-4a03c9821
```

- "Head" refers to the index header and is the distinguishing feature of an index entry.
- "Entry" refers to any entries listed after the index header. "a" means there is an entry in the Alphabetical Section. Numbers refer to entries in the Numerical Section. We refer to these entries with the Entry followed by the Topic in square brackets.
- "Page" refers to a page in the Beehive outside of the Alphabetical and Numerical Sections. If the referenced page can be determined, it is provided in square brackets.

In addition to these metadata categories, the fields "See" and "Add" are used for cross-references in the Index:

![dust](https://stacks.stanford.edu/image/iiif/gw497tq8651%2F1607_0961/419,923,425,114/full/0/default.jpg)

```
Head: dust
See: earth
#item-815d91783
```

![warning](https://stacks.stanford.edu/image/iiif/gw497tq8651%2F1607_0994/1643,2944,631,159/full/0/default.jpg)

```
Head: warning
Entry: 843 [PAGE_MISSING]
Entry: 1060 [Admonishing & Warning]
Add: caution
#item-064de5392
```

The following tags are used to denote problematic entries:

- [PAGE_MISSING] -- the page on which the entry would be is missing from the Beehive
- [WORD_MISSING] -- numerical entry present, word not visible with text
- [INDEX_HEADING_MISSING] -- numerical entry or alphabetic entry present, term not found in index
- [NUMERICAL_ENTRY_MISSING] -- numerical entry referred to not found
- [WORD_ILLEGIBLE] -- numerical entry present, word present but not legible
- [NOT_IN_INDEX] -- numerical entry present, number not referenced in index

In addition to these metadata categories, the following categories are generated while building the site:

- pid: persistent identifier for each annotation, used for paths and correct ordering on the website.
- volume: the volume from the Beehive the annotation is in (e.g. 1, 2, or 3).
- image_number: the image number from a specific volume from the Beehive the annotation is on.
- first_letter: the first letter of the alphabetical entry or index header, or the numerical range of the numerical entry (e.g. 51-100), used for facet browsing.
- unparsed: elements of the annotation not parsed automatically, used in data clean-up and review.

In addition to the core data, the following additional data sets are used in building the site:

- [Alphabetical Sorts](https://github.com/drnelson6/beehive-scripts/blob/master/data/beehive-alpha-sorts.csv)
- [Index Sorts](https://github.com/drnelson6/beehive-scripts/blob/master/data/beehive-index-sorts.csv)

These files provide the "first_letter" metadata used to build the website for alphabetical and index entries, in the case that the entry or head field does not begin with the expected letter (e.g. "False Comfort" is ordered under "C", not "F.")

- [Alphabetical Corrections](https://github.com/drnelson6/beehive-scripts/blob/master/data/alpha-corrections.csv)
- [Index Add Corrections](https://github.com/drnelson6/beehive-scripts/blob/master/data/index-add-corrections.csv)
- [Index See Corrections](https://github.com/drnelson6/beehive-scripts/blob/master/data/index-see-corrections.csv)

These files are used to build cross-references on the website. Because the project follows Pastorius's orthography exactly, only some data will match automatically. In the case that Pastorius cross-references to an entry using a different version of the word than the corresponding entry (e.g. xref "punishmt" should link to entry "Punishment"), the cross-reference and its intended target are recorded here.

- [Alphabetical Issues](https://github.com/drnelson6/beehive-scripts/blob/master/data/alpha-issues.csv)
- [Numerical Issues](https://github.com/drnelson6/beehive-scripts/blob/master/data/num-issues.csv)
- [Index Issues](https://github.com/drnelson6/beehive-scripts/blob/master/data/index-issues.csv)

These files are used to document uncertainties and editorial decisions made while annotating the Beehive and building the site. In the event an annotation has an issue, the issue will appear on its corresponding page.

- [Pastorius pages](https://github.com/drnelson6/beehive-scripts/blob/master/data/pastorius-pages.csv)

This file is used to build the page references. It supplies a list of page references in the Beehive along with their corresponding pid from the Table of Contents. Note that it differs from the page numbers supplied in the Table of Contents in that the fields "pastorius_page_numbers" and "older_pastorius_page_numbers" have been collapsed into one.
