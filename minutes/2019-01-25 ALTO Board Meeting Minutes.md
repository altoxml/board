# 2019-01-25 ALTO Board Meeting Minutes
**Agenda**
1. Welcome new Board Members. [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * [ALTO 4.0: adaptation of "Processing" substructure](https://github.com/altoxml/schema/issues/52) - next steps? [**Jo**]
   * [Schema documentation about use of &lt;SP&gt; needs clarification](https://github.com/altoxml/schema/issues/54) - _Note_: 
Tesseract master branch now exports ALTO, includes &lt;SP&gt; tags [**Clemens**]
   * [Add LANG and ROTATION attributes to Page element](https://github.com/altoxml/schema/issues/55) - recent
4. Touch base on _high priority_ schema issues. [**All**]
   * [ALTO - PAGE xml: Object mapping and possible transformation generation](https://github.com/altoxml/schema/issues/48)
   * [ALTO & IIIF integration](https://github.com/altoxml/schema/issues/45) - 
_Notes from [2019-01-16 IIIF Community Call](https://docs.google.com/document/d/1vCA6UJr5unpJfuxt80a72i9iW0NHPFT8uHeCHLFef_g/edit)_:
      * [IIIF Text Granularity TSG Draft available](https://docs.google.com/document/d/1CCToyJVEr_Gq2R4GuKV5L51hwpCnC1QOYWcIuf0WU5I/edit) - likely to be an extension rather than a core part of the spec at this point, see also 
[Granularities in different OCR formats](https://docs.google.com/document/d/13R7Dk-AA-ALZ5i3fzAS3g66umWjiYaD7NVr8QiYb19E/edit) report
   * [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23)
   * [Reading Order (IMPACT)](https://github.com/altoxml/schema/issues/18)
   * See full list of open schema issues [here](https://github.com/altoxml/schema/issues)
5. Language Discussion:
   * Arabic OCR and Text Representation (Ahmed's connection was lost at the last meeting so bringing this back) [**Ahmed/Hany**]
   * Challenges in the Digitization of Asian Textual Materials [**Cally**]
6. Follow up on upcoming F2F meeting at [DATeCH 2019](http://datech.digitisation.eu/). 
   * Reaching out to Günter Mühlberger and his group at the University of Innsbruck [**Clemens/Stefan**]
   * Existing XML schemas for lattice structures - 
the [ALPS example](https://github.com/altoxml/board/blob/gh-pages/misc/lattice_xml_sample.md) [**Art**]
   * Create Schema issue for use of ALTO for handwriting? [**All**]
7. Other business. [**All**]
8. Next meeting date - proposed: March 22, 2019 [**All**]

**Attending members**
* Ahmed Samir 
* Art Rhyno
* Ashok Popat 
* Cally Law
* Evelien Ket
* Frederick Zarndt
* Hany Abdel Hamid Elsawy
* Joachim Bauer 
* Jukka Kervinen
* Raju Buddharaju
* Stefan Pletschacher

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

* [ALTO 4.0: adaptation of "Processing" substructure](https://github.com/altoxml/schema/issues/52) - The 
[revision](https://github.com/altoxml/schema/blob/master/v4/alto-4-1_draft.xsd)
has been available since September. Art will do a final check with Clemens and then ask the Board to vote on GitHub.

* [Schema documentation about use of &lt;SP&gt; needs clarification](https://github.com/altoxml/schema/issues/54) - 
Based on the Board’s last discussion, there is support for adding a _Content_ attribute to the _SP_ element.  

* [Add LANG and ROTATION attributes to Page element](https://github.com/altoxml/schema/issues/55) - Art will ask for a use case and 
link the issue to the [discussion](https://github.com/altoxml/schema/issues/22) on shape-element usage.

_wrt agenda item 4_. Touch base on _high priority_ schema issues:

* [ALTO - PAGE xml: Object mapping and possible transformation generation](https://github.com/altoxml/schema/issues/48) - 
Christian’s [document](https://docs.google.com/document/d/1cCgHF-FTFkpGRFjZYE0LvvERajiVjJUDePscpN1IExw/edit?usp=sharing) 
is a good start at listing the element mapping between ALTO and PAGE. Stefan’s feeling is that this may no longer be a high 
priority. Ashok asked if ALTO should have the goal of being the unified format for text representation as an alternative to 
encodings like PAGE. Stefan noted that PAGE captures aspects of documents that ALTO does not, and that ALTO reflects its 
origins in the context of METS, where METS encodes the higher level, logical structure of a document.

* [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) - Jo pointed out 
that as the number of OCR engines increase that produce ALTO, the greater the need is for clarity on confidence values. Stefan asked 
if it would be possible to use identifiers to indicate what algorithm was in use and noted that there might be great variations in 
how metrics for glyph and word accuracy are used. Ashok described how his team utilizes an error rate calculated from a development 
set at the character level, that is then aggregated for a coarser granularity. Frederick suggested that the Board provide a standard 
that OCR providers can follow. 

* [Reading Order (IMPACT)](https://github.com/altoxml/schema/issues/18) - As with ALTO-PAGE, this issue reflects a desire for a 
higher level, logical encoding. PAGE supports this functionality and this issue again explores whether there should be overlap
between ALTO and representations like PAGE and METS.

_wrt agenda item 5_. Language Discussion:

* Hany described some of his experience with Arabic OCR. He did extensive work on font libraries at the  Library of Alexander, and 
identified variations in OCR results between bitonal images and color scans. At the Qatar National Library, assigning the proper font 
library has proved to be an important step in digitizing materials, and the workflows there can include machine learning and processes 
that utilize the first few pages of a book for initial testing and training. They have agreed to OCR 8,000 books from the University of 
New York’s Arabic collection and Hany noted that the 
[SHARIAsource project](https://ilsp.law.harvard.edu/shariasource/), which has a kick-off meeting in the next week, may surface 
issues associated with encoding Arabic OCR in ALTO. Frederick would be interested in learning more about the University of 
New York project.

* Cally provided information on the 
[NewspaperSG](http://eresources.nlb.gov.sg/newspapers/) at the National Library of Singapore. NewspaperSG has been in operation for 
nearly a decade, and covers over 200 titles across multiple languages. They have not yet identified an effective OCR solution for 
Tamil and Javanese language materials. Raju will send some options, noting that there some OCR companies in India with this expertise, 
and pointed out that some Indian languages use letters from the Arabic alphabet, such as Urdu and Hindi.

_wrt agenda item 6_. Follow up on upcoming F2F meeting at [DATeCH 2019](http://datech.digitisation.eu/):

* Art will touch base with Clemens about reaching out to Günter Mühlberger for joining the meeting.

* The [ALPS Schema](https://web.archive.org/web/20110118082924/http://xml.comp-phys.org:80/lattice.xsd) 
may provide some ideas on how to represent lattice structures in XML. Ashok will check if any of the internal representation of the 
lattice structure used by the Cloud Vision team can be shared. The lattice is stored internally in a protocol buffer, and represents 
multiple hypotheses, which may have value for handwriting  representation  and Ashok will be able to step through it in person at the 
meeting in DATeCH.

* It was agreed that a Schema issue will be created on the use of ALTO for handwriting in order to provide a starting point for 
discussion. 

_wrt agenda item 8_. The next meeting is tentatively scheduled for March 22, 2019 at 9am EST.               
