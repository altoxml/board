# 2020-06-12 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * time for version 4.2? [**All**]:
      * [Change BASELINE to accommodate a list of points in addition to a single point #32](https://github.com/altoxml/schema/issues/32)
      * [Should FONTSIZE be required? #64](https://github.com/altoxml/schema/issues/64)
   * issue updates: 
      * [ALTO - PAGE xml: Object mapping and possible transformation generation #48](https://github.com/altoxml/schema/issues/48) 
      * [Allow a String to contain alternative Glyph segmentation hypotheses
#57](https://github.com/altoxml/schema/issues/57)
   * full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. OCR quality and transparency in ALTO [**All**] - revisiting [Confidence value calculation #23](https://github.com/altoxml/schema/issues/23) and building on [OCR Confidence in ALTO: Representation, Meaning, Desiderata](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q/edit).
5. ALTO + IIIF [**Frederick**] - see [ALTO & IIIF integration #45](https://github.com/altoxml/schema/issues/45).
6. Summer <del>Face-to-Face</del> Virtual Single Topic Meeting(s):
   * Using an interoperable lattice structure for encoding OCR uncertainty and alternative hypotheses - see [ALTO support for encoding OCR segmentation ambiguity #63](https://github.com/altoxml/schema/issues/63).
   * ALTO for Handwriting - current real-world examples include [Transkribus](https://transkribus.eu/Transkribus/) and [eScripta](https://escripta.hypotheses.org/).
   * Other candidates...
7. Other business. [**All**]

**Attending members**
* Ahmed Samir
* Art Rhyno
* Ashok Popat
* Brian Geiger
* Cally Law
* Ciprian Dinu
* Clemens Neudecker
* Frederick Zarndt
* Hany Elsawy
* Jukka Kervinen
* Matt Miller
* Nate Trail
* Raju Buddharaju
* Ralph Marschall
* Stefan Pletschacher

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * time for version 4.2? - there was general agreement that it was a time for a minor release of ALTO with the two identified issues. Clemens noted that there would soon be a new version  of the [PAGE schema](https://www.primaresearch.org/tools/PAGELibraries) in mid-July and it would be beneficial to align the release schedules. Cip agreed to do the validation and Frederick flagged the need to work with Nate to publish it on the Library of Congress site. The release process should allow time for comments and include documentation about the changes and whether any action was needed for existing ALTO files.

   * [ALTO - PAGE xml: Object mapping and possible transformation generation #48](https://github.com/altoxml/schema/issues/48) - Clemens reported that the contributions to the [prima-core-libs](https://github.com/PRImA-Research-Lab/prima-core-libs) have been been [committed in github](https://github.com/maxnth/prima-core-libs), and that the [OCR-D project](https://ocr-d.de/) has used the code to roundtrip transformations between ALTO and PAGE. Stephan noted that the exercise has been very useful in surfacing issues that would have otherwise been missed, and has helped improve the documentation.

   * [Allow a String to contain alternative Glyph segmentation hypotheses
#57](https://github.com/altoxml/schema/issues/57) - Art stepped through original proposal, noting that the lattice discussion has evolved into [a separate schema issue](https://github.com/altoxml/schema/issues/63) and highlighted the original syntax. It was noted that the creator of the issue has indicated that lattice support would likely address the original request. Clemens pointed out that at least one OCR engine ([Calamari](https://github.com/Calamari-OCR)) seems to support the level of detail required for lattice representation and there was general agreement that this syntax should be optional due to its complexity and possible unavailability.

_wrt agenda item 4_. OCR quality and transparency in ALTO: 

There seems to be a strong interest in this topic, as was evidenced in the recent [Impresso Eldorado newspaper workshop](https://twitter.com/maudehrmann/status/1253313177590419456), as well as the resulting [summary document](https://docs.google.com/document/d/1nYIyuKFLPjgL4VbkKjI338Hh7vy68raCTNoC_vCPT2I/edit). Frederick suggested that this area be separated into two issues, one focused on the representation of the confidence value, and a different issue concerning the confidence itself. The lattice thread is a longer discussion, and a more short-term goal could be encoding the probability of accuracy for OCR with optional information on how the probability has been calculated. Cip pointed out that OCR correction can be flagged in ALTO but it is not connected to the probability metric. Clemens suggested that the ALTO Board can agree on how probability should be represented, but it is up to the OCR provider to decide how to determine this number. On the other hand, providing information on this calculation could be both optional and extremely useful for comparing results from different OCR engines. Art will try to bring together the various threads and documents into one github issue.

_wrt agenda item 5_. ALTO + IIIF: 

Activities round the recent [IIIF Week](https://iiif.io/event/2020/iiifweek/) conference brought forward a number of inquiries on how IIIF could make best use of ALTO, particularly from the IIIF newspapers group. At one point, there was an initiative to create an IETF MIME type for ALTO for use in IIIF, and a number of ALTO-related APIs were proposed. Frederick will follow-up on registering the MIME type and Clemens offered to assist with the formatting challenges. Art will reach out to IIIF to find out the status of the ALTO support within the upcoming version [1.0 Content Search API](https://iiif.io/api/search/1.0/).

_wrt agenda item 6_. Summer Single Topic Meeting(s): 

In recognition of the difficulty in planning f2f events, single topic meetings will be pursued instead. Frederick suggested that video support should be included and Cally flagged the handwriting topic as particularly timely. A tentative date was set for 07-16-2020 for the handwriting discussion, which will include some invited guests. ALTO has gained traction in a number of transcription initiatives and this could be an opportunity to solicit feedback on how the standard can further support handwriting projects.

_wrt agenda item 6_. Other business:

Ashok asked about options for the timing of ALTO Board Meetings. Although the 9am EST timeframe seems to be the best compromise for all of the timezones that the ALTO Board represents, it was agreed that future Board Meetings will target Thursdays instead of Fridays to better meet Board Member’s schedules.
