# 2018-11-29 ALTO Board Meeting Minutes
**Agenda**
1. Welcome new Board Members. [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Arabic OCR and Text Representation: experiences and challenges - we had a great discussion on this topic at the f2f meeting 
in Las Vegas and I think it would be useful for the larger group. [**All**]
4. Spring/Summer F2F Meeting Opportunities - the survey for this would/will normally go out in January but it would be useful to get 
a heads up on conferences/gatherings that should be in the list. [**All**]
5. Review schema issues and other updates. [**Art/Clemens/Jo**]
   * [TextBlocks and paragraphs](https://github.com/altoxml/schema/issues/53)  - can this be closed?
   * [ALTO 4.0: adaptation of "Processing" substructure](https://github.com/altoxml/schema/issues/52) - ready for a vote?
   * [Asian language (Japanese, Korean, Chinese) with ruby characters cannot be properly represented in ALTO](https://github.com/altoxml/schema/issues/51) - is RoleTag sufficient in this case?
   * [Schema documentation about use of &lt;SP&gt; needs clarification](https://github.com/altoxml/schema/issues/54) - see ongoing discussion [here](https://github.com/UB-Mannheim/ocr-fileformat/issues/78)
   * See full list of open schema issues [here](https://github.com/altoxml/schema/issues)
6. Planning for special meeting on handwriting support in ALTO [**All**] - following up on the suggestion at 
the [2018-07-26 ALTO Board Meeting](https://github.com/altoxml/board/blob/gh-pages/minutes/2018-07-26%20ALTO%20Board%20Meeting%20Minutes.md) that we should invite Günter Mühlberger and his group at the University of Innsbruck to meet with the Board about their work on handwriting.
7. Addition of two new Board Members/expansion of Board. [**Frederick**]
8. Other business. [**All**]
9. Next meeting date. [**All**]

**Attending members**
* Ahmed Samir &ast;
* Art Rhyno
* Ashok Popat 
* Brian Geiger
* Clemens Neudecker
* Evelien Ket
* Frederick Zarndt
* Joachim Bauer &ast;
* Jukka Kervinen
* Matt Miller
* Raju Buddharaju
* Ralph Marschall
* Stefan Pletschacher 

&ast; - _lost connection to call early in the meeting_

**Minutes**

_wrt agenda item 3_. Matt gave some background on the [Open Islamicate Texts Initiative]( https://openiti.github.io/) (OpenITI). It 
began a few years ago at a conference in Leipzig, as a result of discussions between Matt, Maxim Romanov, Sarah Bowen Savant and others 
on the need for a machine-actionable scholarly corpus of Islamicate texts. Arabic materials were assembled and Persian texts, which are 
more rare, initially came from the [Ganjoor]( http://ganjoor.net/) poetry collection. The texts are pushed out on github in a Markdown 
format and there has been a realization that stronger OCR options are needed. Benjamin Kiessling, who had worked on OCR for German 
fraktur and was at the initial meeting, assisted in a series of pilot projects using his open source 
[kraken]( https://github.com/mittagessen/kraken) system. The use of _kraken_ has been very effective, and the tests have been 
[published]( https://islamichistorycommons.org/mem/wp-content/uploads/sites/55/2017/11/UW-25-Savant-et-al.pdf), with similar results 
reported from a recent project with JSTOR. OpenITI is interested in a highly retrainable and customizable OCR platform and is working 
with the [SHARIAsource project]( https://ilsp.law.harvard.edu/shariasource/) of Harvard Law School on the creation of a digital text 
pipeline tool called _CorpusBuilder_.

Frederick asked if there issues that Matt has observed which might make the use of ALTO problematic for Arabic materials. Matt has none 
to flag at this point but may know more in a few months. Work will begin using the pipeline on manuscripts in January. Clemens noted that 
his group has a similar workflow pipeline project that Ben has also been involved in, and will send the details to Matt. Frederick asked 
that Ahmed be included in the email and noted that his understanding is that the Library of Alexandria has encountered challenges in 
utilizing ALTO. He believes that most OCR processing there involves the use of 
[Sakhr]( http://www.sakhr.com/index.php/en/solutions/ocr). Matt reported that his work with JSTOR has largely involved hOCR, even though 
ALTO is produced natively by _kraken_. Clemens pointed out that there are tools for round tripping between hOCR and ALTO in 
the [github repository]( https://github.com/cneud/ocr-conversion-scripts) he maintains for OCR conversions. This repository includes 
PAGE conversion tools and Clemens may take up the [ALTO - PAGE issue](https://github.com/altoxml/schema/issues/48) currently marked 
as high priority in the context of the [OCR-D]( http://www.ocr-d.de/) project. 

Art asked about the use of XSLT for OCR conversions. Clemens is not the biggest fan of using XSLT but recognizes its 
platform-independent advantage. Stefan noted that XSLT is the most effective when there is a straight mapping of elements but it is 
sometimes better to use dedicated importers and exporters.

_wrt agenda item 4_. The [DATECH conference](http://openpreservation.org/event/datech-2019) to be held in Bruxelles BEL on 
May 8-10, 2019 may be the strongest candidate for the 
Spring/Summer F2F meeting. Several Board members will be there and it may provide an opportunity to meet with members of 
Günter Mühlberger’s group at the University of Innsbruck to talk about the use of ALTO for handwriting.

_wrt agenda item 5_. Some specific issues were identified for discussion by the Board:

* [TextBlocks and paragraphs]( https://github.com/altoxml/schema/issues/53) – Clemens agreed with Art that the discussion had gone full 
circle on the issue and offered to come up with a concluding remark to the effect that it had been discussed at the Board so that it 
could be closed.

* [ALTO 4.0: adaptation of "Processing" substructure]( https://github.com/altoxml/schema/issues/52) – There was agreement that the 
schema change proposed for this issue is important since it fixes a bug in the current release. Stefan noted that validating the 
schema may not always catch a bug, and that it might be best for Jo to work with the change in development to ensure the bug fix is 
effective. Jukka has been active in the issue and will generate an example document.

* [Asian language (Japanese, Korean, Chinese) with ruby characters cannot be properly represented in ALTO]( https://github.com/altoxml/schema/issues/51) – 
Art has proposed the use of the _RoleTag_ to address this issue, which would not require a schema change. Like the 
[Identification of running title](https://github.com/altoxml/schema/issues/50) issue, the _Tag_ mechanism in ALTO is very useful for 
delimiting components in text without requiring a schema change.

* [Schema documentation about use of <SP> needs clarification]( https://github.com/altoxml/schema/issues/54) – Clemens gave some 
background on this issue, which originates in a long-standing and much desired 
[tesseract pull request for producing ALTO natively from tesseract]( https://github.com/tesseract-ocr/tesseract/pull/2100). The pull 
request is linked to [an issue]( https://github.com/UB-Mannheim/ocr-fileformat/issues/78) of the 
Universitätsbibliothek Mannheim's [ocr-fileformat]( https://github.com/UB-Mannheim/ocr-fileformat) repository. Although it is agreed 
that ALTO does not strictly require the _SP_ element according to the schema, there is ambiguity about whether it is expected. Clemens 
is leaning towards more explicitly stating that it is optional.

   Ashok asked about the handling of different unicode sequences for whitespaces, like the Chinese ideographic space character. Jukka noted 
that the issue had not come up in the decade that he has been serving on the ALTO Board. Some of the comments on the issue suggest 
that it is only a small group that is concerned about capturing whitespace metrics in text, but Jukka pointed out that it can be a 
quality control check. For example, if two adjacent columns have been merged into a text block, the _SP_ element could be used to 
record that there was a _tab_ in the same position. Stefan raised how whitespace is handled in XML, where it is typically stripped 
and then has default handling. Clemens noted that _ABBYY FineReader_ includes the _SP_ element by default, and as a result, it is 
present in many large text collections.

   The handling of hyphenation in ALTO was brought up as a possible model for spaces. The _HYP_ element includes provision for a word 
carrying on into another element. Ashok’s team at Google leans towards a typesetting approach rather than a semantic one, and he 
raised the question of using OCR for the basis of transcriptions. If a Fortan listing was OCRed, would ALTO capture the 6 spaces 
before each command? The _SP_ element includes a _width_ attribute but a human reader would be expected to infer what it denotes 
in this case.

   In response to a question from Frederick, Raju highlighted some of the semantics surrounding spaces in non-latin scripts where a 
word changes meaning based on the spacing. He will provide some examples on github. Matt asked if the Zero-Width Non-Joiner (ZWNJ) used 
in Persian would also be a concern. Clemens responded that the ZWNJ is another example where capturing the unicode sequence is 
important, and Ashok agreed that the focus on unicode might be the best path forward, 
sharing [a link that outlines the variations in spaces supported by unicode]( http://jkorpela.fi/chars/spaces.html). Frederick asked 
about whether the _SP_ element should be language-dependent given that spaces can have unique meaning in some languages, for example, 
the use of space characters to separate vowels in Mongolian. 

   Jukka suggested that adding an optional _CONTENT_ attribute would be useful for future-proofing the _SP_ element, and that perhaps 
the _SP_ element should be a required element in ALTO. There was general agreement that the _CONTENT_ attribute would be useful for 
_SP_ but concerns were raised about enforcing the use of _SP_ in general. Although _FineReader_ exports _SP_ by default, and _docWorks_, 
which makes use of _FineReader_, produces _SP_ elements, there are many ALTO documents without _SP_ and Clemens raised the concern 
about the size of the XML used for ALTO ballooning should _SP_ become a required element.

   Art agreed to try to capture the thread and add it to the github issue since it is clear that this is an ongoing discussion.

_wrt agenda item 6_. As mentioned in _item 4_, Günter Mühlberger’s group is likely to be at DATECH and there is a consensus among the 
Board that exploring the use of ALTO for handwriting is worth pursuing. Clemens noted that Günter and his team are moving away from 
static OCR encoding to confidence matrices for recognized characters and words, an approach similar to Google’s lattice processing. The 
single best hypothesis from an OCR engine may arise downstream as more confidence is created in the domain. Clemens and Stefan are 
both involved in the DATECH conference and will reach out to Günter to confirm availability.

_wrt agenda item 7_. Frederick outlined the strengths that the two recent candidates bring to the ALTO Board, including expertise in 
Chinese, and there was general agreement that the Board should be expanded to accommodate their membership. Frederick will send an 
email to Board members asking for an ACCEPT or REJECT to changing the membership criteria. Expanding a Board can make quorum 
problematic but the ALTO Board largely avoids these kind of governance issue by virtue of using github and email for voting.

_wrt agenda item 9_. The next meeting is tentatively proposed for January 25, 2019 at 9am EST. 
