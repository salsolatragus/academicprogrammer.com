---
title: Extracting Code Segments and Their Descriptions from Research Articles
categories:
  - MSR17
  - ICSE17

---

Code examples from various source, such as StackOverflow or documentation, have been explored to support goals such as code recommendation, comment generation, documentation, or learning from and reusing examples.

Preetha Chatterjee, Benjamin Gause, Hunter Hedinger and Lori Pollock from University of Delaware observe that the IEEEXplore Digital Library contains over 3.5 million full-text publications from electrical engineering, computer science, and electronics. They manually analyzed a random sample of 100 publications from the ICSE, FSE, and ICSME conferences and found that 70% of them contains at least on code example. Since these examples are used to make a point, they presumably contain valuable information. Hence, they developed a tool named CoDesNPub Miner that uses heuristics to identify figures in a paper that actually are code example and relate them to paragraphs that describe these figures.

By manual annotation of 8 research publications with a total of 100 code examples, they evaluate the precision and recall of their tool. The results show that CoDesNPub idenfies roughly every second code snippet (50% recall), while reporting as many false positives as true positives (50% precision). Increasing precision leads to a relatively large drop in recall and vice versa.

This shows that in order to use examples from this source, further improvement of the process in necessary. Furthermore, the approach currently cannot distinguish pseudo code.

[See paper preprint](https://www.researchgate.net/publication/315673133_Extracting_Code_Segments_and_Their_Descriptions_from_Research_Articles)
