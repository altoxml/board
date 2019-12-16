# 2019-12-13 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * ready for a vote [**All**]:
      * [Change BASELINE to accommodate a list of points in addition to a single point](https://github.com/altoxml/schema/issues/32)
   * issue updates: 
      * [ALTO &amp; IIIF integration](https://github.com/altoxml/schema/issues/45)
      * [ALTO support for encoding OCR segmentation ambiguity](https://github.com/altoxml/schema/issues/63) - see [2019-11-03 ALTO F2F Board Meeting Minutes](https://github.com/altoxml/board/blob/gh-pages/minutes/2019-11-03%20ALTO%20Board%20Meeting%20Minutes.md)
      * [Should FONTSIZE be required?](https://github.com/altoxml/schema/issues/64)
      * [Restrict float attribute values where possible to allow for better xml-validation](https://github.com/altoxml/schema/issues/62)
      * [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) - see Ashok's [summary document](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q)
   * full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. Spring Face-to-Face Meeting:
   * confirm event - [Digitised newspapers - a new Eldorado for historians?](https://impresso-project.ch/news/2019/06/12/WS5-CfP.html) Lausanne, Switzerland. April 23-24, 2020
   * possible topics [**All**]
5. Upcoming Board Expirations:
   * _December 31, 2019_: Raju and Stefan
   * _December 31, 2020_: Art, Ashok, Evelien, Jukka, and Ralph
   * _December 31, 2021_: Frederick, Nate, Matthew, and Ahmed Samir
6. Other business. [**All**]

**Attending members**
* Ahmed Samir 
* Ashok Popat
* Art Rhyno
* Christian Clausner
* Ciprian Dinu
* Frederick Zarndt 
* Jukka Kervinen
* Nate Trail
* Raju Buddharaju
* Stefan Pletschacher

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * [Change BASELINE to accommodate a list of points in addition to a single point](https://github.com/altoxml/schema/issues/32) - as per the [2019-09-27 meeting](https://github.com/altoxml/board/blob/gh-pages/minutes/2019-09-27%20ALTO%20Board%20Meeting%20Minutes.md), the issue has been resolved and Art will send a message to the group to confirm that this schema change open for voting.

   * [ALTO support for encoding OCR segmentation ambiguity](https://github.com/altoxml/schema/issues/63) and [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) - Cip described a linkage he made between these two issues in Ashok's [summary document](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q), in that a lattice structure might provide more information for an ALTO processor to compare scores from multiple sources. Ashok noted that confidence metrics are usually rooted in specific and varied algorithms, and there is a need to define something that is simple and general enough to be applied in all cases. He described Google's approach has involved attaching output tokens to the character level and estimating the edit-distance cost to ground-truth. One of the ideas captured in the summary document is to use a heat map attached to the underlying image so that there is an indication of regions where text has not been identified. Christian asked whether linking the issues adds too much complexity given that the original question was how to specify confidence values. Frederick pointed out that standardizing the computation of confidence was rejected in the past because it would be seen as dictating to OCR providers, and that there was general agreement that the goal is to record the factors that led to the confidence scoring. Ashok suggested that one path forward is to leverage the unfolding lattice discussion. As a representation of an n-best list that is weighted, the lattice could provide confidence data that can be computed and help surface use cases, particulary for handwriting recognition. To this end, Art will arrange for a single-topic meeting on OCR segmentation ambiguity in January and invite Gundram Leifert (_Transkribus_) and Robert Sachunsky (_OCR-D_). This will also allow further exploration of the use of lattices and the _confmat_ representation for segmentation, and could align with Ashok's availability in Zürich during the week of January 20, when he might be able to travel to Innsbruck or some other location to physically join the discussion with some of the participants.

   * [ALTO &amp; IIIF integration](https://github.com/altoxml/schema/issues/45) - the recent [IIIF Text Granularity Extension](https://preview.iiif.io/api/text-granularity/api/extension/text-granularity/) might have some overlap with this issue. Art will link the extension to the github discussion.

   * [Should FONTSIZE be required?](https://github.com/altoxml/schema/issues/64) - Christian identified the problem with requiring FONTSIZE in _TextStyle_ as part of his work on [ALTO - PAGE mapping ](https://github.com/altoxml/schema/issues/48). This requirement precludes other style attributes, such as FONTCOLOR, from being encoded if the font size can not be determined. Jukka confirmed that the requirement has been in place since 2009, and that this aspect may have been missed. The issue will be updated with syntax to change the FONTSIZE attribute to _optional_ in the schema so that any concerns can be brought forward.

   * [Restrict float attribute values where possible to allow for better xml-validation](https://github.com/altoxml/schema/issues/62) - Jukka agreed to be champion for this issue. Christian suggested flagging this for the next major release since it could break existing ALTO files, or to document valid float ranges. After some discussion, it was agreed that negative values were valid for rotations.

_wrt agenda item 4_. Spring Face-to-Face Meeting:

Frederick suggested another strong option for the Spring face-to-face meeting could be the [2020 IFLA International News Media Conference](http://iibi.unam.mx/IFLAmedia/) at _Universidad Nacional Autónoma de México_ in Mexico City. There is no limit on f2f meetings if more than one Board member is attending an event, so it is possible that there could be two in the Spring. Stefan, Christian, Clemens and Ashok may be attending [ICPR](https://www.micc.unifi.it/icpr2020/) in Milan, Italy in September 2020, which would make it a good candidate for the Fall face-to-face meeting.

_wrt agenda item 5_. Upcoming Board Expirations:

Raju and Stefan have kindly agreed to continue to serve on the ALTO Board. Ashok anticipates that he will exchange his position on the Board at some point in the next year with someone else from Google. There will be an effort to identify a new Chair before the end of 2020 to allow some overlap and give some time for the transition. Art reiterated what a postive experience it has been for him and thanked Frederick for his mentorship.

The next full Board meeting is tentatively scheduled for Friday, February 14, 2020. The single-topic meeting will hopefully be some time in January if scheduling works out. 
