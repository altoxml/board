# 2020-02-14 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * status changes [**All**]:
      * [Should FONTSIZE be required? #64](https://github.com/altoxml/schema/issues/64) - ready for a vote?
      * [FONTSTYLE: add "strikethrough" to list of allowed values #61](https://github.com/altoxml/schema/issues/61) - ready for a vote?
   * issue updates: 
      * [Allow a String to contain alternative Glyph segmentation hypotheses
#57](https://github.com/altoxml/schema/issues/57)
      * [Reading Order (IMPACT) #18](https://github.com/altoxml/schema/issues/18) 
   * full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. ALTO - PAGE xml: Object mapping and possible transformation generation [**Christian**] - see [associated issue](https://github.com/altoxml/schema/issues/48).
5. Spring Face-to-Face Meeting(s):
   * [2020 IFLA International News Media Conference](http://iibi.unam.mx/IFLAmedia/). March 5-6, 2020. _Universidad Nacional Autónoma de México_. Mexico City.
   * [Digitised newspapers - a new Eldorado for historians?](https://impresso-project.ch/news/2019/06/12/WS5-CfP.html) Lausanne, Switzerland. April 23-24, 2020. The timing and geography could allow both proponents of possible models for encoding OCR ambiguity to participate in person on April 22.
6. Other business. [**All**]

**Attending members**
* Art Rhyno
* Cally Law
* Christian Clausner
* Ciprian Dinu
* Clemens Neudecker
* Evelien Ket
* Hany Elsawy
* Raju Buddharaju
* Stefan Pletschacher

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * [Should FONTSIZE be required? #64](https://github.com/altoxml/schema/issues/64) - there was general agreement that this issue is ready for a vote and Art will change the status to reflect this on github.

   * [[FONTSTYLE: add "strikethrough" to list of allowed values #61](https://github.com/altoxml/schema/issues/61) - Clemens pointed out that there may be additional font styles that are used in other XML schema and volunteered to add this information to the issue.

   * [Allow a String to contain alternative Glyph segmentation hypotheses
#57](https://github.com/altoxml/schema/issues/57) - the OCR segmentation ambiguity aspect has [been moved to a new issue](https://github.com/altoxml/schema/issues/63) and this will likely form the basis of the next face-to-face discussion.

   * [Reading Order (IMPACT) #18](https://github.com/altoxml/schema/issues/18) - this issue is flagged as _high priority_ but has not seen much activity since its creation in 2014.  At that time, the [IMPACT](http://www.impact-project.eu/) project had looked at complex multi-column layouts like newspapers and identified the need for an explicit modeling of reading order in ALTO comparable to that found in PAGE.  The [structMap](http://www.loc.gov/standards/mets/docs/mets.v1-8.html#structMap) element in METS is currently used to encode reading order in some projects, and others use the _IDREF_ in ALTO proper. It is possible that there needs to be documentation rather than changes to the schema. Cip confirmed that _docWorks_ customers have expressed a desire for capturing reading order directly in ALTO and some rely on the default XML rendering. Stefan agreed to champion this issue and noted that the current efforts to encode alternative segmentation scenarios might need to be taken into account.

_wrt agenda item 4_. ALTO - PAGE xml: Object mapping and possible transformation generation:

Christian described his [recent work on an ALTO to PAGE transformation](https://github.com/PRImA-Research-Lab/prima-core-libs/tree/master/java/PrimaDla/src/org/primaresearch/dla/page/io/xml) in the [core java libraries](https://github.com/PRImA-Research-Lab/prima-core-libs) used by the PRImA Research Lab. Clemens pointed out that there has been funding to support a contractor to build on this base, and has added [repository links to the github issue](https://github.com/altoxml/schema/issues/48#issuecomment-586309637). The contract has been for January and February, and the results will eventually be brought back for merging into the Prima core libraries. 

It was noted that PAGE and ALTO serve different purposes. PAGE captures what is literally on the physical page and ALTO encodes the analyzed text. The conversion from one to another will invariably be lossy, but could still be an invaluable starting point for moving between the two formats. 
  
_wrt agenda item 5_. Spring Face-to-Face Meeting(s):

With global health concerns, it is difficult to finalize the arrangements for a Spring date. The tentative plan is to set up a meeting on the afternoon of April 22 as part of the [Impresso](https://impresso-project.ch/news/2019/06/12/WS5-CfP.html) conference but this is subject to current events.

_wrt agenda item 6_. Other business:

The recent [OCR & Digital Text Production: Learning from the Past, Fostering Collaboration & Coordination for the Future conference](https://twitter.com/Open_ITI/status/1222259673459515402), organized by Board member Matt Miller, showcased several projects of interest to OCR researchers, including a novel approach for segmentation that Thomas Breuel is developing for a future version of [OCRopus](https://en.wikipedia.org/wiki/OCRopus), work by Hany on Arabic OCR at the Qatar National Library, and presentations on the challenges of Urdu OCR and automatic transcription for non-latin texts. The report from the conference will be of great interest.

The next Board meeting will be scheduled when the dates for the Spring f2f event are confirmed.
