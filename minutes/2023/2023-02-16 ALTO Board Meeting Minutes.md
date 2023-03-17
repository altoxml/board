# 2023-02-16 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Follow up last meeting topics:
    
  * Voting situation for ALTO schema 4.4 proposals: 
    * Expand schema documentation for PointsType (https://github.com/altoxml/schema/issues/49) - still open, more votes needed
    * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (https://github.com/altoxml/schema/issues/67) - remove xlink, in 4.4 announce it as deprecated

4. New issues to discuss:		

  * Handwritten documents and ALTO encoding - how to make ALTO more suitable for such documents - ideas (https://github.com/altoxml/schema/issues/81) - topics proposals
 
5. Face-to-face meeting new proposal: ICDAR 2023, San José, US 21-26 August 2023 [**All**]

  * Other proposals are welcomed
  * Intention is to make it a hybrid meeting so that everybody can attend

6. Other business. [**All**]

**Attending members**
* Brian Geiger
* Ciprian Dinu
* Frederick Zarndt
* Sebastien Cretin
* Thomas Haighton
* Cally Law
* Raju Buddharaju
* John Loitzenbauer
* Hany Abdel Hamid Elsawy

 **Minutes**

 * Review of proposed changes for version 4.4
    * Add LANG and ROTATION attributes to Page element (altoxml/schema#55) - clarified, nothing to discuss, implement proposed changes
    * Storing detected languages (altoxml/schema#66) - clarified, nothing to discuss, implement proposed changes
    * Expand schema documentation for PointsType (altoxml/schema#49) - from the presented options, initially most voted was Option 2 (four ways to describe a list of points). Lately more votes for Option 1 were expressed (two ways to describe a list of points, more restrictive). The arguments in the favor of Option 1 were that in fact these are the most used in practice, other options were not used in practice and is not a good idea to increase complexity, when is not needed. Topic was discussed in the meeting and everybody agreed that, even Option 2 looked better initially, the arguments for Option 1 are good enough to change the initial opinion. Option 2, with brackets may be easier to parse, but still is better not to encourage new ways to encode a points list. Everybody was also in favor to add a supplemental recommendation, to prefer comma format, rather than the one only with spaces as separators (even this should be kept since tools like Kraken are still using it)
    * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (altoxml/schema#67) - remove xlink is the current proposed solution, there were no concerns on this. More than this looks like on METS board they have same approach for the future
  * New ideas to discuss related to handling of handwritten text
    * We get in contact with FamilySearch and ask for a feedback regarding their needs in regards to ALTO. For future we could ask one of their members to join ALTO Board
    * One proposed idea: https://github.com/altoxml/schema/issues/83 - option to enrich ALTO content by extending with other existing schemas (similar with metadata records in METS). Two samples described - mathematical formulas and musical scores, but mainly any other specific formats could be used (other idea would be any specific family records from ancestry industry). Question is if this exceeds or not ALTO scope.
    * Discussion regarding the possible option to allow full text at any level (Textblock, Textline, etc.)- Thomas mentioned this is not a good idea, since may create a lot of issues regarding file size and consistency. It was agreed that ALTO mainly should serve to its original purpose, not as a format for keeping groundtruth data (as PAGE)
    * Frederick mention as use case to take into account the mixed documents - printed text and handwritten text (f.e. adnotation on a printed text, as well filled forms). Other information that could be encoded in ALTO for printed forms is for example the link between description of the field (printed) and the value of the field (hand written text, checked or not check-box, etc).
    * Frederick asked if we know where else is ALTO used, except libraries and archives. He also mentioned as similar format for text encoding HOCR (used by Tesseract) - could be interesting to find out who else is using it and how. Hany mentioned they used to use it to encode Arabic text. Currently there is a project at Qatar National Library to switch to ALTO. There are a lot of challanges specially on Arabic handwritten text, on manuscript. They evaluate Sotoor, as well British library evaluate same engine for Arabic OCR.
  * Face to face meeting
    * ICDAR 2023, San José, US 21-26 August 2023 - remains the only proposal, option could be DATeCH in December 2023  
 
