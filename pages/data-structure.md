---
layout: page
title: Beehive Data Structure
permalink: '/data-structure/'
---

### About the Alvearium Data Model

The Digital Beehive Project uses a Mirador annotation server to create the linked entries of the Alvearium, a section of the Beehive. Each annotation is linked to a canvas, which is defined as a page from the Beehive. An individual page of the Alvearium may contain as many as 15 entries. The Beehive data can be viewed at the whole page level, or at the level of individual entries. 

The core data for the Digital Beehive Project consists of the annotations and canvases created in the Mirador server. These annotations provide minimal metadata that copy, as accurately as possible, the content of the Beehive.

### Beehive Entries

The Alvearium contains a section of entries arranged alphabetically by topic, as well as a section of entries that Pastorius arranged by number. Additionally, most entries of the Alvearium are listed in an index that Pastorius composed as a separate octavo codex.

A typical annotation from the Alphabetical Section looks like this:

![Witchcraft](https://stacks.stanford.edu/image/iiif/fm855tg5659/1607_0532/320,2567,3027,466/full/0/default.jpg)
```
Entry: Witchcraft
Topic: Witchcraft
Xref: 1312 [Witchcraft]
Index: witchcraft
#item-6d7b3a01f
```
A typical annotation from the Numerical Section looks like this:
![1465 [Malabarians]](https://stacks.stanford.edu/image/iiif/fm855tg5659/1607_0763/896,3842,2844,1125/full/0/default.jpg)
```
Entry: 1465
Topic: Malabarians
Xref: 1461 [Alms]
Xref: 1421 [Atheism]
Xref: 1681 [Creation]
Xref: 55 [Metempsychosis]
Xref: 1680 [Images]
Xref: 1683 [Heaven]
Xref: 1256 [World]
Xref: 1329 [Perfection]
Xref: 1685 [Malabar]
Xref: 1044 [Books]
Xref: 1607 [Soul]
Xref: 971 [Senses] 
Page: p.233 [Image 1.384] 
Page: p.234 [Image 1.385]
Index: malabaria
#item-a5b22479c
```
### Anatomy of a Beehive Annotation
##### Viewing individual annotations

- Boxes are drawn to include the full text of the entry. In order to capture that full text, boxes for one entry may also contain some of the previous or subsequent entries from the same page of the Alvearium. In general, any text (typically cross-references) that appears above the line dividing entries belongs to the previous entry, even if it is visible in the annotation canvas of the next topic.

##### Topics
- For alphabetical entries, "Entry" and "Topic" are typically identical. They refer to the underlined title of the entry. For numerical entries, "Entry" refers to the number assigned to the entry, and "Topic" refers to the underlined descriptive title of the entry.

##### Cross-references
- "Xref" lines denote all cross-references, i.e. references to other entries in the Alvearium. Cross-references may occur either directly to the right of the underlined topic, at the end of the entry, or in the body of the entry text. 
- Cross-references are generally indicated by the presence of words like "Add", "See" and "Vide" (adde infra, vide supra, num. anteced. etc), but may also appear as just a word or number.
- If Pastorius writes only a word or phrase as a cross-reference, and this word or phrase corresponds to an entry from the alphabetical section of the Alvearium, then it is assumed that this cross-reference refers to the corresponding alphabetical entry.
- If Pastorius writes only a word or phrase as a cross-reference, but this word does not correspond to any entry from the alphabetical section of the Alvearium, then the cross-reference links to the first numerical entry relevant to the topic and includes a note explaining this decision as part of the annotation. Another way of handling these cases would be to omit any cross-reference link and simply record the word or phrase without a link. After some deliberation, the project team chose to apply the former protocol.
- If Pastorius writes a number as a cross-reference, it is assumed this refers to a numerical entry, and we include that number along with the topic for the corresponding entry. If the cross-referenced numerical entry appears on a missing page, we write [PAGE_MISSING] in lieu of a topic.
- Occasionally, Pastorius writes an apparent cross-reference that does not correspond to any extant entry in the Alvearium. In these instances, we make a note of the problem in our annotation.

##### Index
- If an entry in the Alvearium appears in the Octavo Index of the Beehive, then our annotation of the alphabetical or numerical entry links to the corresponding index entry. In the annotation, "Index" refers to the corresponding index entry and matches the “Head” field for the corresponding item in the index. Note that entries may be referred to multiple times in the index, or not at all. When an entry in the Alvearium does not appear in the index, we still write an "Index" line in our annotation but write [NOT_IN_INDEX] in lieu of a "Head."

##### Page references
- A "Page" refers to a page in the Beehive outside of the Alphabetical and Numerical Sections. Generally, Pastorius uses page references to refer readers to items on his book lists that are relevant to the content of the entry in the Alvearium. If the page reference can be determined, we note both the page number (according to Pastorius's own numbering system) and the image number in our digitized manuscript. Note that Pastorius sometimes writes a list of books that spans multiple pages but only names the first page. In these instances, we write page references that link to all pages on which items from book lists appear. At this time, we do not have a protocol for linking to individual entries from book lists, only to the pages on which they appear.
- Occasionally, Pastorius refers to items from the Onomastical section of the Beehive. We express these references as page references, referring to the pages from the Onomastical section that contain the items that he refers to. Future progress on the Digital Beehive may involve annotating entries in the Onomastical section and creating a specific protocol for linking to them.

##### Item numbers
- The item tag is a randomly generated, unique identifier and is used in building the site. Item tags do not appear on the Digital Beehive web interface but can be found in our datasets.

##### Marginalia
![1453 [Mad]](https://stacks.stanford.edu/image/iiif/fm855tg5659/1607_0761/884,2359,2859,612/full/0/default.jpg)
![1454 [Reproof]](https://stacks.stanford.edu/image/iiif/fm855tg5659/1607_0761/895,2873,2816,689/full/0/default.jpg)
- Some entries have symbols in the margins, such as asterisks, lines or hash marks. This marginalia is generally understood to indicate semantic links (as above), or to distinguish which specific entry is intended to be cross-referenced in cases where multiple topics share the same entry number.


![4455 [Some short Rhimes]](https://stacks.stanford.edu/image/iiif/fm855tg5659/1607_0900/407,3759,2968,346/full/0/default.jpg)
- Pastorius also added capital R's in the margins of some entries. One numerical entry in the Alvearium, 4455 [Some short Rhimes], explains that some of those R entries contain "Some short Rhimes," but it is not clear whether every appearance of an R is indicative of rhyme. Previous project teams believed the R's to denote references to works enumerated in one of Pastorius’ book lists.

### The Octavo Index
A typical annotation from the Octavo Index looks like this:

![bible](https://stacks.stanford.edu/image/iiif/gw497tq8651%2F1607_0953/1090,234,517,134/full/0/default.jpg)

```
Head: bible
Entry: a
Entry: 421 [Bible]
Page: p.41 [Image 1.101]
#item-4a03c9821
```


- "Head" refers to the index header and is the distinguishing feature of an index entry.
- "Entry" refers to any entries from the Alvearium that are listed after the index header. An "a" means there is an entry in the Alphabetical Section. Numbers refer to entries in the Numerical Section. We refer to these entries with the Entry followed by the "Topic" in square brackets.
- "Page" refers to a page in the Beehive outside of the Alphabetical and Numerical Sections. If the page reference can be determined, we note both the page number (according to Pastorius's own numbering system) and the image number in our digitized manuscript.



In addition to these metadata categories, the fields "See" and "Add" are used for cross-references within the Index itself:

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

##### Crochets
Because the Alvearium is organized alphabetically, Pastorius created a system for inserting index entries in their proper alphabetical place, most likely after he had run out of space to do so. Occasionally, Pastorius enters a number in square brackets. For instance, next to "to tremble" on [image 3.48](crochets001.jpg) of the Octavo Index, Pastorius writes ["[:13.]](crochets002.jpg)." All of the numerical 'crochets' in the Octavo Index refer to a page called "Some Additional words between two Crochets,"" which appears on [image 3.54](https://kislakcenter.github.io/digital-beehive/toc/toc3_54/) of the Octavo Index, which lists the heads of the 'crochet' entries and their associated Alvearium entries (where, for instance, it is revealed that [:13.] is "trespass"). There are 63 of these crochets in total.


### Exception codes
The following tags are used to denote problematic entries:

-```[PAGE_MISSING]```-- the page on which the entry would be is missing from the Beehive
-```[WORD_MISSING]```-- numerical entry present, word not visible with text
-```[INDEX_HEADING_MISSING]```-- numerical entry or alphabetic entry present, term not found in index
-```[NUMERICAL_ENTRY_MISSING]```-- numerical entry referred to not found
-```[WORD_ILLEGIBLE]```-- numerical entry present, word present but not legible
-```[NOT_IN_INDEX]```-- numerical entry present, number not referenced in index


### Inconsistencies
- The Alvearium and index were annotated by many hands over the course of many years. We have attempted to regularize the annotations according to our protocol and to the best of our abilities, but annotation protocols, use of exception codes, and interpretations of Pastorius' intentions have all changed over time, and inconsistencies may appear in the data, particularly with regard to linkages to manuscript sections outside of the Alvearium.