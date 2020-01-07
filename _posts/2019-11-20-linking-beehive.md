---
layout: post
title: "Linking the Beehive: Technical Considerations"
author: drnelson6
tags: [blog]
description: How do we use Python to create linked entries for Pastorius's Beehive?
---

Pastorius's "Beehive" manuscript contains numerous cross-references between entries. An early goal of the Digital Beehive was to hyperlink these entries, allowing the user to automatically navigate Pastorius's system of reference. Pastorius, however, has numerous irregularities in his manuscript, and these irregularities have in turn become part of our dataset. In this blog post, I am going to think through some of the technical difficulties of creating these hyperlinks and discuss the challenges that remain.

First, however, let's consider why we are creating these links in the first place and how we know what they are. All sections of the Beehive feature cross references. Pastorius guides the reader from one individual entry to any number of related entries. In the Alphabetical and Numerical Sections, Pastorius indicates a cross reference through use of the word "Add.":

![Pastorius's entry "Commandments"](https://stacks.stanford.edu/image/iiif/ps974xt6740%2F1607_0442/339,648,3120,495/full/0/default.jpg)

Here, we can readily identify three cross-references. At the top of the entry, we see references to "Forbidden things" and "Prohibition." At the end of the entry, he links to "1041" in the numerical section. Since "Forbidden things" and "Prohibition" don't have numbers of special markings, we assume Pastorius intends to link to another entry in the alphabetical section. If we scan the Beehive for corresponding entries, we find this is indeed the case:

![Pastorius's entry "Forbidden things"](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0479/779,3707,2941,464/full/0/default.jpg)

![Pastorius's entry "Prohibition"](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0510/361,3531,3004,348/full/0/default.jpg)


How can we create links between these entries? Fortunately, because they are both in the Alphabetical Section, and we have already annotated the Alphabetical Section, we know that pages exist for these entries on our website. We also know that they will have predictable URLs. For the purposes of creating pages, we assign each item a unique "pid" (persistent identifier) and a collection. The URL will be the base URL for the site, plus the collection and the pid. The entry "Forbidden things" has the pid 'alpha_0338' and is part of the collection 'alpha2'. We thus know we need to append '/alpha2/alpha_0338/' to the end of the site's base URL to access the entry "Forbidden things." If we write the cross-reference in our source file in the HTML format for a hyperlink, it will create the desired link. So we need to replace the cross-reference "Forbidden things" with \<a href='/New_Beehive/alpha2/alpha_0338'>Forbidden things</a> in our source data.  

To do this individually for each entry would be impossible. It would take too long and the risk of incorrect data entry is too great. Not only that, we need to periodically reprocess the data as we are constantly correcting, improving, and expanding our data collection. Fortunately, it is relatively easy to write some code that will create these links for us. Using Python's _pandas_ library, we can easily query and manipulate our dataset. You can see the full version of the code on my [Github](https://github.com/drnelson6/beehive-scripts), but here's a simplified version of the basic operation:

```python
import pandas as pd
import re

def alpha_annotator(item, ref):
    '''
    This function will create links in HTML syntax to alphabetical
    entries in the Beehive
    '''
    pid = item['pid'].to_list()
    pid = pid[0]
    first_letter = item['first_letter'].to_list()
    first_letter = first_letter[0]
    if first_letter.startswith(('A', 'B', 'C', 'D')):
        return f"<a href='/digital-beehive/alpha1/{pid}/'>{ref}</a>"
    elif first_letter.startswith(('E', 'F', 'G', 'H')):
        return f"<a href='/digital-beehive/alpha2/{pid}/'>{ref}</a>"
    elif first_letter.startswith(('I', 'K', 'L', 'M', 'N')):
        return f"<a href='/digital-beehive/alpha3/{pid}/'>{ref}</a>"
    elif first_letter.startswith(('O', 'P', 'Q', 'R', 'S')):
        return f"<a href='/digital-beehive/alpha4/{pid}/'>{ref}</a>"
    else:
        return f"<a href='/digital-beehive/alpha5/{pid}/'>{ref}</a>"

with open('beehive-data.csv', 'r') as f:
  df = pd.read_csv(f)

for row in df.index:
  xref = df.loc[row, 'xref']
  xref_match = df[df['entry'] == xref]
  try:
    annotation = alpha_annotator(xref_match, xref)
    df.loc[row, 'xref'] = annotation
  except IndexError:
    print(f'{xref} does not match!')

new_csv = df.to_csv('beehive-data-linked.csv')
```

The collection for each item is determined by the first letter of the entry. In order to separate items out into the correct collection, we have to find the first letter and then assign the correct URL. In order to match up cross-references and entries, we can see query the column of entries to see if there is a match. Pandas returns a series, which we convert to a list to extract only the relevant information. It is possible that there are multiple or zero matches. In any case, indexing the list at the zeroeth position solves the problem. If there are multiple entries, we normatively assume only the first is correct. If there are no matches, we will get an error. We can then have the script print out the bad xref, and possibly other relevant metadata, which we can use to correct problems in the data. Once we have a match, we just need to extract the pid and first letter from the data in order to create the annotation.

If Pastorius's data were neat and perfect, all of the entries would link like magic. Unfortunately, Pastorius never expected that his Paper-Hive would be manipulated computationally, and much of his raw input works very poorly for this code. We made the decision early on to keep his spelling and capitalization. Thus, if Pastorius forgets to capitalize a cross-reference, it won't link automatically:

![Pastorius's entry "Too much"](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0526/344,2948,3001,585/full/0/default.jpg)

In the above entry, Pastorius does not capitalize the cross-reference for "abundance." Since the entry "Abundance" is capitalized, it will not link automatically as pandas searches for an exact match. We have three options for correcting this. The first would be to regularize the data. We could add either a new column for regularized data or place a regularized token in brackets next to irregular data. It would then be easy to write code that uses the regularized data in place of Pastorius's often messy spellings. In the future, it may very well make sense to do this, but for the moment, it would take more effort to correct the data already collected than to try to computationally correct for these issues. Another option would be to write code to regularize the source data. This is also undesirable as we want to preserve Pastorius's spellings as much as possible. The third option is thus to manipulate how data is matched in order to correct for errors. Fortunately, capitalization is relatively easy to correct:

```python
for row in df.index:
  xref = df.loc[row,'xref']
  xref_match  = df[df['xref'].str.lower() == xref.lower()]
```

Here, we change both the entry we are searching for and the cross-reference to a lowercase version of the word without rewriting the original data. We can thus correct for any irregularities in Pastorius's capitalization practices. The code, however, becomes increasingly complex and difficult for a human reader to parse.

But what do we do with more complex inconsistencies? Numerous abbreviations and irregularities abound in Pastorius's Beehive. Some abbreviations are relatively common. For example, Pastorius frequently uses 'mt' to abbreviate the suffix 'ment', as we see in the entry for "New Testamt":

![Pastorius's entry "New Testament"](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0525/755,1457,3052,490/full/0/default.jpg)

We can use the ".replace()" method in python to correct for such things:

```python
for row in df.index:
  xref = df.loc[row,'xref']
  xref_match = df[df['entry'].str.lower() == xref.lower().replace('mt','ment')]
```

But already, our code becomes quite complex and difficult to parse. And there are several additional abbreviations that we would also need to correct for.

Pastorius also uses a number of irregular abbreviations. These abbreviations are obvious to a human reader but quickly become computational nightmares. If Pastorius wants to link to a related word or idea, he will often only write the first few letters, allowing the reader to supply the missing suffixes:

![Pastorius's entry 'Possibility'](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0508/337,2950,3042,478/full/0/default.jpg)

![Pastorius's entry 'Patience'](https://stacks.stanford.edu/image/iiif/fm855tg5659%2F1607_0506/298,1629,3068,508/full/0/default.jpg)

In these two entries, we see Pastorius cross-reference to an abbreviated form of the main entry's negative counterpart. For "Imposs," he leaves it to the reader to supply the suffix "-ibility," and for 'Pat,' '-ience.' It would be possible for computationally correct for these, asking the code to check for the cross-reference plus a list of corresponding suffixes. For relatively common suffixes, like "-ness" and "ion," this makes sense, as we will be able to handle multiple entries simultaneously this way. However, for abbreviated suffixes that occur only once in our data set, like these two examples, we gain no benefit from trying to regularize the data in this way. It would be just as easy to check individually for the irregular word or to even manually add the link. And even when abbreviating the same word, Pastorius can be inconsistent:

![Pastorius's entry for 'Discipline'](https://stacks.stanford.edu/image/iiif/ps974xt6740%2F1607_0449/807,985,2972,520/full/0/default.jpg)

Here, Pastorius uses both "disc." and "discipl." as abbreviations for "discipline." It would not be easy to write a single correction to handle both.

As the Beehive remains a relatively small dataset for the moment, we can write a script that will individually check for known irregular spellings and automatically connect them with their corresponding entries. The advantage of writing this as code over manually adding the cross-references is that we reduce the chance for human error and can replicate our work when we need to reprocess the data. This, however, is a tedious task and is not an ideal solution as our dataset continues to grow and become richer and more complex.
