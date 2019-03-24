# 2019-03-22 ALTO Board Meeting Minutes
**Agenda**
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Getting revision to ALTO 4.0 out the door - 
see [ALTO 4.0: adaptation of "Processing" substructure](https://github.com/altoxml/schema/issues/52) [**Jo**]
4. Review recent schema issues:
   * [Allow a String to contain alternative Glyph segmentation hypotheses](https://github.com/altoxml/schema/issues/52) [**Art**]
      * [example with glyph variant](https://github.com/altoxml/board/blob/gh-pages/misc/alternative_sample.md)
   * [ALTO for Handwriting](https://github.com/altoxml/schema/issues/56) [**All**]
   * [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) [**Jo**]
   * See full list of open schema issues [here](https://github.com/altoxml/schema/issues)
5. Follow up on upcoming F2F meeting at [DATeCH 2019](http://datech.digitisation.eu/) - May 8-10, 2019 (May 7 for meeting?)
   * Reaching out to Günter Mühlberger and his group at the University of Innsbruck [**Clemens/Stefan**]
   * Scoping out an agenda: handwriting, supporting multiple hypotheses [**All**]
6. Other business. [**All**]
7. Next meeting date - proposed: May 7, 2019. _Note_: this is the F2F meeting and dependent on room availability/etc. [**All**]

**Attending members**
* Ahmed Samir 
* Art Rhyno
* Cally Law
* Frederick Zarndt
* Hany Abdel Hamid Elsawy
* Joachim Bauer 
* Jukka Kervinen
* Matt Miller

 **Minutes**

_wrt agenda item 3_. Getting revision to ALTO 4.0 out the door - Jukka agreed to take a final look at the the revision and will 
notify Art that it is ready for a vote on github.

_wrt agenda item 4_. Review recent schema issues:

   * [Allow a String to contain alternative Glyph segmentation hypotheses](https://github.com/altoxml/schema/issues/52) - 
   Jukka noted that he also has the need to encode multiple hypotheses and uses a custom schema that adds attributes to the 
   _ALTERNATIVE_ element in order to add word confidence. Jo wondered if the existing variant support for glyphs could 
   cover this use case. Frederick pointed out that ALTO files can grow exponentially when supporting variants. Jo
   brought forward the conclusion from a previous discussion on supporting multiple ALTO files, that a version control system 
   is a better approach to managing variant files. It was agreed that this issue needs futher exploration and will become more 
   important for potential handwriting support in ALTO.

   * [ALTO for Handwriting](https://github.com/altoxml/schema/issues/56) - Ahmed and Hany confirmed that there is a synergy 
   between using ALTO for Arabic and the handwriting use case. The example used for the issue has overlapping coordinates at the 
   gylph level, which ALTO supports, and puts additional pressure on the need to clarify the confidence metrics in ALTO. Cally 
   described the work that [NewspaperSG](http://eresources.nlb.gov.sg/newspapers/) does with crowdsourcing transcriptions of 
   Javanese, and asked about how best to identify that text is handwritten, typeset, and/or crowdsourced in ALTO. Jo noted that 
   METS has a role in storing information from transcription workflows and that ALTO's processing support can have a role in 
   documenting the history of how text has been produced in addition to information about the OCR engine. Hany and Jo both 
   flagged the difficulties around coordinate assignment with transcriptions and translations, where there is not always a 
   character-to-character match. Frederick described how Veridian can correct existing crowdsourced or translated text, and Jo 
   pointed out that CCS has a workflow system for supporting corrections.

   * [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) - The 
   issue proposes an upcoming single topic meeting and some description was provided on previous events of this type. The champion for 
   an issue is a key participant, the meeting is opened to anyone interested in the topic, and the outcomes of meeting would normally be 
   documented with the issue in github. It was agreed that it would be best to hold this meeting before the face-to-face meeting at 
   DaTECH. Art volunteered to send out a doodle poll and will propose several dates with the goal of having it occur in April.

_wrt agenda item 5_. Stefan communicated to Art that he will send an introductory email to the DaTECH organizers, as well as to Günter, 
so that the particulars of the meeting can be confirmed. There was general agreement that handwriting is a timely topic to focus on 
at the meeting, and that the multiple hypotheses and confidence value issues are important components of the discussion.

_wrt agenda item 6_. Matt was asked about the initial meeting of 
the [SHARIAsource project](https://ilsp.law.harvard.edu/shariasource/) that occured a few weeks ago. He reported that that 
the meeting went well and will investigate whether the proposal that led to the Mellon grant for the project can be shared with 
the Board.

_wrt agenda item 8_. The next meeting will be the F2F gathering at DaTECH, most likely on May 7, 2019.
