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
