# 2022-12-15 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Follow up last meeting topics:
  * Voting situation for ALTO schema 4.4 proposals: 
    * Support for script in addition to language (https://github.com/altoxml/schema/issues/70) - voting (propose to close)
    * Add LANG and ROTATION attributes to Page element (https://github.com/altoxml/schema/issues/55) - voting (proposed changes available on https://github.com/altoxml/schema/pull/77)
    * Storing detected languages (https://github.com/altoxml/schema/issues/66) - voting (proposed changes available on https://github.com/altoxml/schema/pull/77)
    * Expand schema documentation for PointsType (https://github.com/altoxml/schema/issues/49) - still open
  * Proposals for ALTO schema 5.0
    * Restrict float attribute values where possible to allow for better xml-validation (https://github.com/altoxml/schema/issues/62) - still open - propose for 5.0 due to back compatibility issues)
    * Restrict PointsType to a well defined format (https://github.com/altoxml/schema/issues/80) - implementation itself
    * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (https://github.com/altoxml/schema/issues/67) - remove xlink more feedback needed

4. New issues to discuss:		
  * ALTO schema 4.4 release proposal (time frame)
  * Handwritten documents and ALTO encoding - how to make ALTO more suitable for such documents - ideas (https://github.com/altoxml/schema/issues/81) - topics proposals
 
5. Face-to-face meeting new proposal: ICDAR 2023, San José, US 21-26 August 2023 [**All**]
  * Intention is to make it a hybrid meeting so that everybody can attend

6. Other business. [**All**]
  * Membership expire at the end of 2022 for: Clemens, Cip, Raju, Stefan

**Attending members**
* Brian Geiger
* Ciprian Dinu
* Frederick Zarndt
* Jukka Kervinen
* Stefan Pletschacher
* Sebastien Cretin
* Thomas Haighton

 **Minutes**

 * Topics on voting, proposed for 4.4:
    * Add LANG and ROTATION attributes to Page element (altoxml/schema#55)
    * Storing detected languages (altoxml/schema#66)
    * Expand schema documentation for PointsType (altoxml/schema#49) - more votes are needed for a final decision (how restrictive should be the schema: there are three options - high level restriction, medium level restriction - favorite option till now, low level restriction)
 * Topics to be closed (no changes into schema, but decided to close the topics):
    * Support for script in addition to language (altoxml/schema#70)
 * Topics to be included into 5.0 version (that will break back compatibility):
    * Restrict float attribute values where possible to allow for better xml-validation (altoxml/schema#62) - still open - propose for 5.0 due to back compatibility issues)
    * Restrict PointsType to a well defined format (altoxml/schema#80) - implementation itself depends on (altoxml/schema#49)
    * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (altoxml/schema#67) - remove xlink is the current proposed solution, till now no concerns coming from community/ALTO board. Frederick suggested to ask KBNL if they use xlink, for the cases when there is no METS file that "links" in a logical way various ALTO blocks. Thomas mentioned that he is not aware of this case on KB, they always use METS/ALTO. Jukka proposed to mark this as deprecated in 4.4 and let the community that will be removed in 5.0. In case somebody have any issue with this will probably contact us.

* New topics to discuss:
   * Next topic discussed was related to Handwritten documents and ALTO encoding - how to make ALTO more suitable for such documents. A topic was created to collect ideas and topics to be discussed (https://github.com/altoxml/schema/issues/81). Cip mentioned two topics as a result of Transkribus feedback: allow text content on any level not only on String level (with a restriction, content should be optional info, but should not replace full structure till string level, we may end up into "plain text ALTO" files) and use ALTO also as a format to create data training for OCR (similar with PAGE). Jukka proposed to use tags to record different text authors - this might be relevant into the context of handwritten text, since the handwritten is different for each individual person. Stefan raised two interesting topics, being involved in both PAGE and ALTO "worlds" - one thing is that the usage of ALTO and/or PAGE depends a lot on the tools availability and the choice to use one or the other is driven by this, probably more than the format itself. Second is a discussion regarding the original purpose of each format (ALTO/PAGE) - what is their main purpose, and does it makes sense to try to replicate features one format has into the other, or let mainly both formats evolve independently, following their initial goal. ALTO is intended to present a result (text and layout as a result of OCR mainly) while PAGE was developed more for ground truth data collection, for research, experiments, etc. Stefan mentioned also some problems regarding the option to have content on multiple levels - this could lead to inconsistencies between text on one level and text on levels below (it should be the same) but the PAGE schema f.e. do not enforce this in any way, the tools creating PAGE are the one that try to enforce/validate this. Because the PAGE was used for GT creation, and people usually take care on this data to be checked/validated it was decided that "multi-level content" is more useful than problematic. On ALTO this may be completely different on the other way, the final users (libraries) would not expect such inconsistencies, specially that ALTO result could be a combination between human interaction and machine results. This is one sample why would be good to always have in mind the purpose and usage for each of these formats. Frederick asked if we know more use cases from users dealing with handwritten text. Cip mention about handwritten registers, f.e. birth/marriage/death registers, but there the output format is not ALTO, people are more interested into records containing custom fields and relation between records, rather than full page layout and text. Jukka mentioned about handwritten library cards as possible use case, but there probably the information is more relevant as record, with custom fields, rather than layout and full page text. Sebastien mentioned some issues on their tests on BNF materials using custom segmentation and Kraken OCR engine - the generated ALTO looks quite messy (more a problem with the tools rather than the format itself). Thomas asked what other formats are used for handwritten text, and how good these formats answers specific problems of handwritten text (f.e. PAGE). Stefan outlined again that is imported the usage - f.e. for ALTO there were a lot of discussions in the past regarding variants for text - quite useful for an "internal working format" like PAGE, but in fact not relevant for a library f.e. that is interested into displaying the best possible result and nothing more. We should go with the discussion into this direction: how we can improve ALTO to encode better handwritten text as best possible and useful information for a presentation system. Stefan mentioned that maybe we may think on some features for handling materials where records/links are important, where ALTO is not that useful in particular. Cip mentioned that probably something like named entity tags to point to external records/URL could be useful. Frederick mentioned about FamilySearch and share the link (https://www.familysearch.org) where we can play around with their system and maybe get some ideas. Stefan mentioned that we need to get as many as possible use cases from libraries and final users, not necessary to see things from developers perspective and try to add all ideas that these might have for easier development of tools. Frederick mentioned that maybe we can get on board somebody from FamilySearch so that we get their view on historical records, and what ALTO features may be useful since they are a huge player into handwritten documents world. Sebastian mentioned that they intend to process French manuscripts from XVIII-XIX century, letters and own/personal notes of French writers. Jukka mentioned about lecturer notes, manuscripts, clandestine/forbidden books. Cip mentioned about original manuscripts of writers, with a lot of annotation, but also some more "technical" manuscripts like Einstein notes, or other mathematicians/physicians/etc. - these may not be easy to encode using current ALTO format. Thomas mentioned that on KBNL they have just scanned some handwritten materials and maybe would be a good idea to share these on github as samples.
	
* Face-to-face meeting proposal [**All**]
  * ICDAR 2023, San José, US 21-26 August 2023. Any other proposals are welcomed so that we organize the meeting where most of the members will be able to join. 
	* Intention is to make it a hybrid meeting so that everybody can attend
	* Propose as "one topic" meeting - "Handwritten documents and ALTO encoding" - how to make ALTO better suitable for handwritten documents (after collecting ideas/proposals)

* Other business [**All**]
  * Last topic concerns the membership, since four memberships are about to expire at the end of 2022: Cip and Stefan confirm that they will continue for the next two years interval. Clemens and Raju membership will expire too, this will be clarified soon as well.
  * **A HAPPY NEW YEAR!**
