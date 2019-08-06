# 2019-07-08 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) - 
   making Ashok's [summary document](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q) more widely 
   available. [**Ashok**]
   * candidates for closing [**All**]:
      * [ALTO 4.0: adaptation of "Processing" substructure](https://github.com/altoxml/schema/issues/52) 
      * [textBlock "writing-mode" proposal](https://github.com/altoxml/schema/issues/12)
      * [Position for rotated text](https://github.com/altoxml/schema/issues/59)
   * seeking champions [**All**]: 
      * [Add LANG and ROTATION attributes to Page element](https://github.com/altoxml/schema/issues/55)
      * [Schema documentation about use of `<SP>` needs clarification](https://github.com/altoxml/schema/issues/54)
      * [Reading Order (IMPACT)](https://github.com/altoxml/schema/issues/18)
   * See full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. Alternative hypotheses and lattice support discussion [**All**] -  pursuant to the consensus at the 
[F2F Brussels meeting](https://github.com/altoxml/board/blob/gh-pages/minutes/2019-05-07%20ALTO%20Board%20Meeting%20Minutes.md) 
to "encode multiple hypotheses within a standard and interoperable lattice structure", background material includes:
   * [_confmats_ model](https://github.com/CITlabRostock/CITlabConfMat) from the University of Rostock
   * [Allow a String to contain alternative Glyph segmentation hypotheses](https://github.com/altoxml/schema/issues/57) and 
   related OCR-D issue - [allow intermediate PAGE annotation for word segmentation ambiguity](https://github.com/OCR-D/spec/issues/72)
   * [Capturing complex workflow provenance](https://github.com/altoxml/schema/issues/47)
   * [Length of main glyph and variants](https://github.com/altoxml/schema/issues/44)
5. Potential F2F Board meeting at [2019 DLF Forum](https://forum2019.diglib.org/) - afternoon of 2019-10-13 in Tampa, Florida. [**All**]
6. Other business. [**All**]

**Attending members**
* Ahmed Samir 
* Ashok Popat
* Art Rhyno
* Brian Geiger
* Cally Law
* Evelien Ket
* Frederick Zarndt
* Hany Abdel Hamid Elsawy
* Jean-Philippe Moreux
* Joachim Bauer 
* Jukka Kervinen
* Matt Miller
* Nate Trail
* Ralph Marschall
* Raju Buddharaju

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) - a link to 
   Ashok's [summary document](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q) will be added to this 
   issue, and the document will be shared with other groups. Nate volunteered to send on the link to the NDNP mailing list and comments 
   can be made directly on the google doc.

   * candidates for closing:
      * [ALTO 4.0: adaptation of "Processing" substructure](https://github.com/altoxml/schema/issues/52) - this has been implemented in 
      version 4.1 and Jo will close.
      * [textBlock "writing-mode" proposal](https://github.com/altoxml/schema/issues/12) - Evelien suggested that this can probably be 
      closed and Art will follow up with Clemens to confirm that this is the case.
      * [Position for rotated text](https://github.com/altoxml/schema/issues/59) - Jo noted that HPOS and VPOS always refer to the 
      top-left position of the element. This will be left open.
      
   * seeking champions - Board members are encouraged to become a champion for issues not currently assigned to anyone, and the 
   three identified in the agenda are good starting points.

_wrt agenda item 4_. Art described how the lattice discussion dovetailed with the interest in using ALTO for encoding handwriting. Jo 
flagged the complexity in supporting handwriting, noting that the variants inherent in handwriting recognition can lead to significant 
overhead in parsing and processing. ALTO’s user base lies largely in the cultural heritage community and the encoding is currently 
human readable. If the files were to mushroom in size and need representation in different formats for processing, there would be need 
for a JSON or streamlined version of ALTO. Jo will create 
[a schema issue proposing the creation of standardized format for large-scale encodings](https://github.com/altoxml/schema/issues/60).

Ashok provided more details on the lattice modeling used at Google, where nodes correspond to locations in the line, and edges correspond 
to character hypotheses which, in turn, are annotated with the optical character match score and the language model score. He noted 
that the language modeling has turned out to be useful in improving accuracy, for example, there might be a URL pattern present in 
the text that can be leveraged in recognition. 

Frederick asked if there was value in standardizing confidence metrics before exploring lattices. Ashok highlighted the prospect
identified at the [DATeCH meeting](2019-05-07%20ALTO%20Board%20Meeting%20Minutes.md) of deriving standard 
confidence numbers from lattices, and suggested that lattice support in ALTO could be usefully investigated at the same time. An 
example of a text line with a lattice representation corresponding to Google's modeling will be added to the github 
issue to help frame the discussion.

_wrt agenda item 5_. Another candidate location for the Fall F2F meeting is the upcoming 
[2019 IIIF Working meeting](https://iiif.io/event/2019/ann_arbor) to be held November 4-7 in Ann Arbor, Michigan. Frederick will 
check if meeting room arrangements can be made for this event.

_wrt agenda item 6_. Ashok brought forward a new scenario regarding confidence metrics for consideration. In cases where an estimated 
degree of contribution is assessed for a character based on its location, the lack of a character in the location could lower the 
confidence calculation. There is nothing to associate this calculation with in ALTO because there is no gylph to reference. 
Ashok noted that this problem may possibly be sidestepped by providing a lattice structure if the confidence can be derived 
from it, though it may also be more susceptible to deletion errors.

An initiative that has been forwarded to the Board regarding an abstract system of textual "coordinates" that are centred around 
digital texts, and which is connected to TEI and IIIF in addition to ALTO, will be tracked as more details emerge. The researchers 
are putting together a background document which will be useful for determining how ALTO might be impacted by this project.

The next meeting is tentatively scheduled for September 27, 2019 at 9am EST.
