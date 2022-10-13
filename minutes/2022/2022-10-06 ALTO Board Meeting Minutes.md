# 2022-10-06 ALTO Board Meeting Agenda
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Follow up last meeting topics:
    * Support for script in addition to language (https://github.com/altoxml/schema/issues/70) - voting (propose to close)
    * Add LANG and ROTATION attributes to Page element (https://github.com/altoxml/schema/issues/55) - voting (proposed changes available on https://github.com/altoxml/schema/pull/77)
    * Storing detected languages (https://github.com/altoxml/schema/issues/66) - voting (proposed changes available on https://github.com/altoxml/schema/pull/77)
    * Restrict float attribute values where possible to allow for better xml-validation (https://github.com/altoxml/schema/issues/62) - still open - propose for 5.0 due to back compatibility issues)
    * Expand schema documentation for PointsType (https://github.com/altoxml/schema/issues/49) - still open - propose for 5.0 due to back compatibility issues; documentation to be updated in 4.4

4. Issues to discuss:
    * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (https://github.com/altoxml/schema/issues/67)
    * Confidence value for Layout detection of elements (https://github.com/altoxml/schema/issues/69)
	
5. Face-to-face meeting proposal: DATeCH 2022, Alicante, Spain 12-14 Dec. 2022 [**All**]

	* Intention is to make it a hybrid meeting so that everybody can attend
	* Propose as "one topic" meeting - "Handwritten documents and ALTO encoding" - how to make ALTO better suitable for handwritten documents 

6. Other business. [**All**]

**Attending members**

* Raju Buddharaju 
* Ciprian Dinu 
* Hany Abdel Hamid Elsawy
* Jukka Kervinen
* Cally Law
* John Loitzenbauer
* Clemens Neudecker
* Frederick Zarndt

 **Minutes**
 
Review of topics discussed last time:

* Support for script in addition to language: https://github.com/altoxml/schema/issues/70 - xsd:language mainly supports also the script encoding into language encoding using standards like BCP47 or older RFC1776 mechanism. Topic is proposed to be closed, voting is in progress

* Add LANG and ROTATION attributes to Page element: https://github.com/altoxml/schema/issues/55 - LANG and ROTATION on Page level should represent the default value for these two fields, with option to be overwritten on lower levels (blocks, lines, string, etc). Proposed change can be found in pull request https://github.com/altoxml/schema/pull/77. Voting is in progress

* Storing detected languages: https://github.com/altoxml/schema/issues/66 - this topic is related with the previous one and it propose a solution to outline from the beginning, on the PAGE level, what languages an user should expect on that particular page. This is a list with all the languages found on the page, compared with LANG attribute from previous topic that represent the default language for that page. Proposed change can be found also in pull request https://github.com/altoxml/schema/pull/77. Voting is in progress

* Restrict float attribute values where possible to allow for better xml-validation: https://github.com/altoxml/schema/issues/62 - the topic is related to restrictions to ALTO coordinates. There are many coordinates values that should be restricted to positive values or clear defined ranges (f.e. rotation angles float values between 0 and 360 degrees). This change will be only possible to be implemented in 5.0 since will break back compatibility. We will provide a schema proposal that will address this topic. There is still an open question if is possible to have restrictions relative to other values (f.e. a block position should not be outside page bounding box). This is possible with Schematron validation, but not clear if there is any option when using xsd validation. Clemens will ask other people from community if they know of any possible solution.

* Expand schema documentation for PointsType: https://github.com/altoxml/schema/issues/49 - based on the discussions on the topic, we should have this split into two parts - one would be a good candidate for version 4.4 - add into documentation the recommendation of how a polygon should be encoded and announce intention of adding restrictions starting from version 5.0 and second part adding restriction itself (since this will break compatibility, should be in 5.0). There is still one opened question - how many options we should allow: very restrictive (maximum 2 options), medium level (four options) or still allow a lot of flexibility (6-8 or more ways to encode a point set). Cip will add a comment to the topic and ask for board members opinion for a vote between three options (very restrictive, medium restrictions, very relaxed). Clemens mentioned that there is a difficult decision to take, each will have advantages and disadvantages. He could ask OCR-D community as well for a feedback. Cally mentioned that probably a medium restriction would be ok. An e-mail to ALTO mailing list could be useful to collect as many as possible opinions

New topics to be discussed:

* Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions: https://github.com/altoxml/schema/issues/67 - till now there were two proposals for solving this, one inspired by PREMIS (with an additional proposed variant) and one inspired by a proposal from METS board. Jukka mentioned that he is not aware if the METS proposals was adopted or not into METS schema. During the meeting we figure out that a third solution might be the best one - simply remove xLink completely since it looks is not really used (or at least the meeting participants could not remember any use case). We need to ask the community if and how is use it, before taking a decision. 

* Confidence value for Layout detection of elements: https://github.com/altoxml/schema/issues/69 - a quite interesting topic, but in the same time quite complex one. The main issue is related to a proper "layout analysis confidence" definition, what it means, how it can be defined. One problem is to define a reference, a ground truth - what means a "correct analysis"? Cally mentioned that we need a "base" to compare, is a much more subjective evaluation than in the case of a text. Clemens mentioned that also on other groups the definition of ground truth for layout analysis is no clear defined. There are different metrics (like IoU or others), but none can really fully capture the quality of the analysis. He mentioned that layout analysis has in fact two components - segmentation and classification, each of them could lead of different categories of errors. Current segmentation/classification methods do not provide any type of confidence. An accuracy can be computed based on a ground truth, but if ground truth is missing is not clear how a confidence could be computed, taking into account the multitude of solutions and technologies involved into this topic (pixel based classifications, transformers, heuristics - rules-based systems or hybrid approaches). Nevertheless such a feature would be helpful to select for example pages with "probably not good layout analysis" based on confidence in order to perform QA and corrections on those pages, instead of doing QA on the entire data set (similar with text correction based on text confidence). We can keep the topic open, and check more feedback on the communities dealing with segmentation tasks in order to understand if such a measurement could be feasible.

Face-to-face meeting:

* The proposal for face-to-face meeting was to be organized as hybrid meeting on DATeCH 2022, 12-14 December, Alicante, Spain. Clemens mentioned that even is not official it might be that the conference will not take place as originally planned, and will probably shifted for May/June 2023. In December it might be that they will organize a two days meeting for people from community (people from IMPACT competence center, some libraries, etc), but not a real conference. Due to this we need to see other options and probably postpone this year and find other options for the future. By the end of October 2022 we should have a clear decision (depending also on DATeCH official notification), but most probable the face-to-face meeting will not take place this year as intended. Possible next best option would be ICDAR 2023, end of August 2023.

* Regarding the proposed topic for face-to-face meeting (Handwritten documents and ALTO encoding - how to make ALTO more suitable for such documents) Clemens mentioned that it could be a very good idea since important players from the community (Transkribus and eScriptorium) have a lot of users and these do not use ALTO, but adapted versions of PAGE format. Cip will open a thread on github to collect ideas related to this topic.
