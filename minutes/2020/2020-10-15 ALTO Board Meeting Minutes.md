# 2020-10-15 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * handwriting support: 
      * [Reading Order #18](https://github.com/altoxml/schema/issues/18)
      * [Schema documentation about use of SP needs clarification #54](https://github.com/altoxml/schema/issues/54)
   * updates:
      * [Storing detected languages #66](https://github.com/altoxml/schema/issues/66)
   * full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. Next steps for longer-term issues: 
   * OCR quality and transparency in ALTO - revisiting [Confidence value calculation #23](https://github.com/altoxml/schema/issues/23) and building on [OCR Confidence in ALTO: Representation, Meaning, Desiderata](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q/edit).
   * Using an interoperable lattice structure for encoding OCR uncertainty and alternative hypotheses - see [ALTO support for encoding OCR segmentation ambiguity #63](https://github.com/altoxml/schema/issues/63).
5. Upcoming Board Expirations:
   * _December 31, 2020_: Art, Ashok, Evelien, Jukka, and Ralph
   * _December 31, 2021_: Frederick, Nate, Matthew, and Ahmed Samir
6. Other business. [**All**]

**Attending members**
* Ahmed Samir
* Art Rhyno
* Brian Geiger
* Cally Law
* Clemens Neudecker
* Frederick Zarndt
* Hany Elsawy
* Nate Trail
* Raju Buddharaju
* Ralph Marschall

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * [Reading Order #18](https://github.com/altoxml/schema/issues/18) - Clemens gave some background information on the issue, describing it as an artifact from the [IMPACT project](https://www.digitisation.eu/) and a desire to emulate the mechanism in [PAGE-XML](https://github.com/PRImA-Research-Lab/PAGE-XML) for indicating the sequential reading order of text. PAGE allows the grouping of regions in both ordered and unorderd groups compared to ALTO's more limited IDNEXT option for encoding sequences. Newspaper digitization projects have traditionally punted to METS for this functionality but there is growing interest in capturing reading order in standalone ALTO files, particularly for supporting handwriting. Clemens will flag this issue in the [OCR-D project](https://ocr-d.de/).

   * [Schema documentation about use of SP needs clarification #54](https://github.com/altoxml/schema/issues/54) - Art will write up a proposal based on the consensus in the [2018-11-29 Board Meeting](https://github.com/altoxml/board/blob/gh-pages/minutes/2018/2018-11-29%20ALTO%20Board%20Meeting%20Minutes.md) that an optional _CONTENT_ attribute to the _SP_ element would help address the concerns over the encoding of [different unicode sequences for whitespaces](http://jkorpela.fi/chars/spaces.html), like the Chinese ideographic space character. A _content_ attribute would allow the use of [character entity references](https://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references) and possibly open up the use of the _gylph_ element.  
   
   * [Storing detected languages #66](https://github.com/altoxml/schema/issues/66) - Art noted @bertsky's [github commment](https://github.com/altoxml/schema/issues/55#issuecomment-511056317) on the the potential of `xsd:list itemType="xsd:language"` to allow a comma-delimited list in ALTO in the same manner as PAGE. Clemens pointed to the difficulties of encoding languages, arising from automated language detection, that have been encountered at the Berlin State Library, and Ahmed and Cally described how the main language of a document would often be encoded for the collections they work with. Frederick offered to identify some examples from _Chronicling America_, where multiple languages have been encoded in multilingual newspapers.

_wrt agenda item 4_. Next steps for longer-term issues:

   * OCR quality and transparency in ALTO - Clemens suggested that a white paper on confidence value calculations might be a good way to proceed. The white paper could build on [Ashok's discussion paper](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q/edit). Frederick will reach out to [ABBYY](https://www.abbyy.com/) to encourage participation in the dialogue. The growing importance of being able to compare OCR engines was recognized, especially when ground truth is not available. Clemens noted that ABBYY now supports version 3 of ALTO, which seems to be a fairly recent change.

   * Using an interoperable lattice structure for encoding OCR uncertainty and alternative hypotheses - the extensive [proposal](https://github.com/altoxml/schema/issues/63#issuecomment-550991423) put together by @bertsky has not seen much recent activity and Clemens will provide some updated contact information so that this can move forward.  
   
_wrt agenda item 5_. Upcoming Board Expirations: 

Evelien has indicated that she will be stepping down at the end of her term. Ralph will be continuing. 

_wrt agenda item 6_. Other business:

Art asked the members of the Board to consider taking on the Chair position when his term expires at the end of December, and noted that it is a very positive experience, especially given the great depth and experience of the group. Anyone interested in the position should reach out to him or Frederick.
