# 2021-02-25 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * reopened: 
      * [Length of main glyph and variants #44](https://github.com/altoxml/schema/issues/44)
   * new:
      * [Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions. #67](https://github.com/altoxml/schema/issues/67)
   * full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. Confidence Calculations Redux: 

   The [ALTO Schema 4.2](http://www.loc.gov/standards/alto/v4/alto-4-2.xsd) currently defines accuracy/confidence in the following ways:
   | Name | Element | XSD | Scale | Annotation |
   | --- | --- | --- | --- | --- |
   | Accuracy | Page | attribute | 0-100 &#8594; | Estimated percentage of OCR Accuracy in range from 0 to 100 |
   | PCType | Page | simpleType (used for PC attribute) | 0-1 &#8594; | Page Confidence: Confidence level of the ocr for this page. A value between 0 (unsure) and 1 (sure). |
   | WCType | String | simpleType (used for WC attribute) | 0-1 &#8594; | Word Confidence: Confidence level of the ocr for this string. A value between 0 (unsure) and 1 (sure). |
   | CC | String | attribute | 0-9 &#8592; | Confidence level of each character in that string. A list of numbers, one number between 0 (sure) and 9 (unsure) for each character. |
   | GC | Gylph | attribute | 0-1 &#8594; | This GC attribute records a float value between 0.0 and 1.0 that expresses the level of confidence for the variant where 1 is certain. This attribute is optional. If it is not available, the default value for the variant is “0”. The GC attribute semantic is the same as the WC attribute on the String element and VC on Variant element. |
   | VC | Variant | attribute | 0-1 &#8594; | This VC attribute records a float value between 0.0 and 1.0 that expresses the level of confidence for the variant where 1 is certain. This attribute is optional. If it is not available, the default value for the variant is “0”. The VC attribute semantic is the same as the GC attribute on the Glyph element. |

   _CC example_:
   ```xml
   <String HPOS="5485" VPOS="4654" WIDTH="468" HEIGHT="109" CONTENT="quorum" WC="1.00" CC="211110"/>
   ```
   | Character | Confidence |
   | --- | --- |
   | q | 2.0 |
   | u | 1.0 |
   | o | 1.0 |
   | r | 1.0 |
   | u | 1.0 |
   | m | 0.0 |

   _Background materials_:
   * OCR quality and transparency in ALTO - [Confidence value calculation #23](https://github.com/altoxml/schema/issues/23) and [OCR Confidence in ALTO: Representation, Meaning, Desiderata](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q/edit).
   * Using an interoperable lattice structure for encoding OCR uncertainty and alternative hypotheses - see [ALTO support for encoding OCR uncertainty and alternative hypotheses #63](https://github.com/altoxml/schema/issues/63).
   * [XML deprecation discussion](https://stackoverflow.com/questions/1950075/mark-element-as-deprecated-in-xsd) (_Stack Overflow_)
5. Board membership:
   * _December 31, 2020_ expirations: Art, Ashok, Evelien, Jukka, and Ralph (Art, Jukka and Ralph renewed, Ashok to be replaced by Reeve? ideas for Evelin's replacement)
   * _December 31, 2021_: Frederick, Nate, Matthew, and Ahmed Samir
   * Chair position available
6. Other business. [**All**]

**Attending members**
* Ahmed Samir
* Art Rhyno
* Cally Law
* Christian Clausner
* Ciprian Dinu
* Clemens Neudecker
* Frederick Zarndt
* Hany A. Abdellatif
* Jukka Kervinen
* Raju Buddharaju
* Ralph Marschall
* Sébastien Cretin

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * [Length of main glyph and variants #44](https://github.com/altoxml/schema/issues/44) - Clemens gave some background information on the issue, it has resurfaced in the OCR-D project where composed characters and graphene clusters are hitting the limit currently in the schema. It is unclear whether allowing unlimited values is also problematic and additional  feedback is requested.
   * [Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions. #67](https://github.com/altoxml/schema/issues/67) - Frederick noted that he has observed that ALTO schemas sometimes will not validate, and it could be because of xlink and network connectivity. Jukka is using local references, and confirmed that the same xlink issue has been raised in the METS Board.

_wrt agenda item 4_. Confidence Calculations Redux:

Frederick described how some of the schema may reflect long-standing use of ABBYY. Clemens flagged the increased use of OCR-correcting systems,
which tend to work at the character level and can make good use of accuracy metrics. Cip questioned whether the suggestion put forward in the gitub issue
regarding dropping _CC_ and encoding character level accuracy with the _glyph_ element was always viable, given the resulting expansion in the size of the ALTO
file. Cally noted how the _CC_ element provides a short-hand way of viewing the confidence for each character but wondered how critical this is since
more systems parse these values  at a machine level. Clemens has not seen use cases in OCR-D where the _glyph_ element would not provide better data than
_CC_. Art asked if there was value in expanding the documentation for _CC_ to flag its deficiencies. XML Schemas do not have a prescribed method of
deprecating syntax but there is scope to highlight the strengths and limits of different encodings.

Clemens noted that projects which reference accuracy metrics for items or collections are more likely to base the statements on the page confidence or some calculation
on individual word confidences. He is working on a paper for the ICDAR conference on inconsistencies in accuracy use between characters and words, and hopes for some
feedback from implementers, particularly OCR tool developers that are tasked with populating the numbers that are put forward. Numbers from neural-network based
OCR engines, like Calamari, are difficult to fit into the same metrics. 

Art asked about the page confidence scale, which is different from the 0-1 scale used elsewhere in the schema. Frederick described how the page value
had the goal of providing one place to look to get a sense of the overall confidence metric. Cip noted that the page value is usually a sort of average
value but that there is no prescribed method for its calculation. Clemens described how one of the appeals of working at the character/glyph level
for accuracy is that it avoids the dictonary aspects associated with word confidence, which is problematic for engines that use a machine learning approach
rather than a lexicon-based process. Cip raised the question of whether it would be useful to emphatically state that the scales for confidence are 
linear, noting that some engines don't use normalized values.

_wrt agenda item 5_. Board membership:

Art will reach out to Nationale Bibliotheek van Nederland for a possible replacement for Evelien's position, and Board members are encouraged to put names forward.

_wrt agenda item 6_. Other business:

Clemens made a plug for the upcoming [ICDAR](https://icdar2021.org/) conference, to be held in Lausanne, Switzerland, on September 5-10, and which will have both an in-person and virtual component. The next Board meeting will likely be held in April.
