# 2023-05-04 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Topics to discuss:
    
    * Next major version 5.0 - there are several issues that require a major version: 
      * Restrict PointsType to a well defined format (https://github.com/altoxml/schema/issues/80) - implement restrictions defined in  (https://github.com/altoxml/schema/issues/49)
      * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (https://github.com/altoxml/schema/issues/67) - remove xlink, announced on schema 4.4
      * Restrict float attribute values where possible to allow for better xml-validation (https://github.com/altoxml/schema/issues/62) - discuss all similar cases and break it down to multiple topics if needed
      * Deprecate and then remove ZORDER/IDNEXT since from 4.3 we have a different mechanism for order (https://github.com/altoxml/schema/issues/82) 
      * CC attribute to be deprecated (https://github.com/altoxml/schema/issues/72)
4. Major feature proposal for 5.0:		
* Probably might be good to have something related to handwritten encoding in ALTO - we are still into ideas collection phase
    * Other proposals
 
5. Face-to-face meeting new proposal: probably ICDAR 2023, San José, US 21-26 August 2023 [**All**]
* A survey was sent with two choices ICDAR 2023 and DATeCH 2023 
    * Intention is to make it a hybrid meeting so that everybody can attend
    * Decision should be made by 15th of June
6. Other business. [**All**]

**Attending members**
* Thomas Haighton
* Cally Law
* Ciprian Dinu
* Clemens Neudecker
* Ashok Popat
* Raju Buddharaju
* Jukka Kervinen

**Minutes**
* Proposals for next version (small topics, but changing back compatibility):
   * As the next version was proposed 5.0 since there are several topics on issues list that will break back compatibility and might be a good time to make this major version change. The option to release 4.5 version was discussed, if is needed, or not, and the conclusion was that we may add an intermediary version if we figure out there is a need (for example to fix any issue in previous version, etc.) but we should aim for 5.0 as next version. Following topics implementation will change back compatibility: 
   * Restrict PointsType to a well defined format (https://github.com/altoxml/schema/issues/80) - implement restrictions defined in  (https://github.com/altoxml/schema/issues/49) - topic is opened for proposals regarding regular expression that should be used for enforcing the new PointsType format.
   * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (https://github.com/altoxml/schema/issues/67) - change was already announced and will be implemented (no feedback from community with any concern)
   * Restrict float attribute values where possible to allow for better xml-validation (https://github.com/altoxml/schema/issues/62 - a review is needed in order to check all places where restrictions should be added. One open topic is to find a solution for relative restrictions (f.e. coordinates should always be smaller than page width/height which is not a fixed value). Jukka mentioned it could be possible to be implemented in xsd schema version 1.1. Jukka will check and add more information regarding this topic and also make a first schema proposal. Clemens mentioned that in practice he could see some negative coordinates and we need to careful check all these cases to ensure we do not have any valid cases that break this rule. Cip mentioned such a case, space between two words using very skewed italic font, depending on what it means "space width" this might be negative (doesn't mean the negative value was ok, but is a sample case of possible problems that may occur if restrictions are enforced)
   * Deprecate and then remove ZORDER/IDNEXT since from 4.3 we have a different mechanism for order (https://github.com/altoxml/schema/issues/82) - the proposal looks ok, but as Clemens mentioned would be a good idea to prepare some use cases/documentation for existing mechanism (proposed in 4.3). Clemens will check with OCRD community for some specific samples (manuscripts, documents with hand written annotations, etc.) and Cip will check for some newspaper pages samples. Clemens mentioned about the documentation created by Evelyn some years ago for ALTO tags and polygonal shapes (http://altoxml.github.io/documentation/use-cases/tags/ALTO_tags_usecases.html and http://altoxml.github.io/documentation/use-cases/shape/ALTO_shape_usecases.html) 
   * CC attribute to be deprecated (https://github.com/altoxml/schema/issues/72) - this attribute was not announced yet as deprecated and is still used a lot in practice. Idea of removal was based on the fact that same information can be outline as glyph confidence. The downside of this is that whenever the information is needed, the file size overhead will be quite big, while glyphs info grows a lot ALTO file size, compared with simplified attribute CC on word level. Historically the glyphs idea was proposed in order to have additional information for post-processing of the text, and came together with other ideas like variants and segmentation hypotheses. Clemens mentioned that in the last time OCR engines became so good that automatic post-processing is not something very useful and efficient. Ashok mentioned that even a lattice based information bring some advantages is not very practical to encode it as xml in order to pass it to a post-correction engine and since OCR engines are better and better this idea does not look that interesting anymore. 

* Proposals for main features of 5.0
  *   Handwritten documents and ALTO encoding - how to make ALTO more suitable for such documents - ideas (https://github.com/altoxml/schema/issues/81) - place holder for initial ideas collection, to be later on base for other issues
  *  Option to enrich ALTO content description (https://github.com/altoxml/schema/issues/72) - add into ALTO the possibility to embed other custom formats to describe more accurate formulas, music scores, etc. that are now encoded as simple Illustration. Jukka proposed to tie in a composed block an illustration and this additional description. Ashok was wandering if the purpose of OCR is to extract the semantics of symbolic representation in a textual/graphical image so that a system can render this and the users do not need to look on the image pixels anymore. Probably topics like this will change a bit the purpose of ALTO, initially intended as a format to represent OCR text from a page, into a format to semantically describe the full content of the page. Clemens mentioned he knows some use cases for both formulas or music scores. Other ideas - embedded maps with geographic coordinates, electronic schemas, hand written annotation, etc. Jukka asked about the general table of representation - currently composed blocks with cells as text blocks could be used, order could be a good idea to add. By this new proposal, other smarter representations could be imagine (add structure information like rows/columns, etc.). This type of feature could make ALTO more versatile as Jukka mentioned. 

* Face to face meeting
  * ICDAR 2023, San José, US 21-26 August 2023 - remains the only proposal, DATeCH in December 2023 does not look too probable. A decision should be taken by 15th of June in order to have enough time to organize  

