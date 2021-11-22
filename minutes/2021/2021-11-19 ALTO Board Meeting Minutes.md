# 2021-11-19 ALTO Board Meeting Minutes
1. Welcome - with special guests [Benjamin Kiessling](https://github.com/mittagessen) and [Robert Sachunsky](https://github.com/bertsky) [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Open discussion of _Schema Pull Request_ - [Direction, orientation, and reading order (text direction elements) #74](https://github.com/altoxml/schema/pull/74). [**All**]
4. Upcoming Board Expirations:
   * _December 31, 2021_: Frederick, Nate, Matthew, and Ahmed Samir
5. Other business. [**All**]

**Attending members**
* Art Rhyno
* Ashok Popat
* Cally Law
* Ciprian Dinu
* Hany A. Abdellatif
* Jukka Kervinen
* Raju Buddharaju
* Thomas Haighton

**Participating guests**
* Benjamin Kiessling
* Robert Sachunsky

 **Minutes**

_wrt agenda item 2_. Open discussion of _Schema Pull Request_ - [Direction, orientation, and reading order (text direction elements) #74](https://github.com/altoxml/schema/pull/74):

Ben presented the proposed changes to the schema and described the challenge of encoding scripts that can be written in different orders (vertical and horizontal, left-to-right and right-to-left) on the same page. Robert asked about the granularity at which base direction could be set and Ben noted the difficulties of going beyond lines for dealing with blank spaces and sentence structures, especially since the [BDI algorithm](https://unicode.org/reports/tr9/) is best applied to lines.

The reading order proposal closely reflects the approach in [PAGE-XML](https://github.com/PRImA-Research-Lab/PAGE-XML) while allowing the ordering of subtext block elements. This complicates parsing but it supports capturing more semantics for text blocks and text lines. Ben showed an [example](https://msia.escriptorium.fr/media/documents/955/PGPID_952_MS-TS-00013-J-00014-00013-000-00001.jpg) with two different commentary blocks as well as interlinear text. The interlinear text would be encoded as a text line under the proposal, and could be inserted into the line based on the reading order. Tags can be assigned to the reading order elements, for example, the _Role_ tag could be set to _correction_. Another [example screenshot](https://files.gitter.im/608fd2096da03739847ba370/bsqf/image.png) showed how humanists are currently using arrows to indicate insertions. He also went through a [sample page](https://upload.wikimedia.org/wikipedia/commons/5/52/Complutensian_Polyglot_Bible_-_Genesis_1.1.png) that contains several languages. The text blocks are independent and would best be encoded in unordered groups, a scenario which is also common in many newspapers. The ability to encode multiple reading-orders is of particular value to humanists, where there can be divergent opinions on the order of the text in manuscripts.

Cip noted that there could be several approaches to handling the interlinear text, including encoding the text as a standalone line and also within the line it applies to. Ben raised the difficulty of using pointers and other solutions that referenced positions within a line. Individual characters could arguably be insertions as well, and it could quickly become overly complex to apply position information while switching between words and glyphs. He also identified the lack of standard examples for ALTO to address such scenarios. 

It was agreed that it should be possible to have a valid ALTO processor without  necessarily parsing a specific reading order, and that the current _IDNEXT_ mechanism would also need to continue to be supported moving forward. Ben noted how rare the use of _IDNEXT_ seems to be in ALTO files and compared it to the limited use of _BASELINE_ before ALTO was used for handwriting. Robert questioned if scenarios based on text direction could always be resolved by reading order, for example, when interlinear text identifies corrections, a structured tag might be more suitable. Art asked about lessons that could be learned from the use of PAGE-XML for reading order and it was noted that most deployments fall back to the explicit element order of the encoding, whether it be PAGE-XML or ALTO exported from platforms like _Transkribus_ or _eScriptorium_, or ALTO and hOCR output from OCR engines like Tesseract. 

Cally shared a link to a [newspaper example](https://www.nas.gov.sg/citizenarchivist/Newspaper/Transcribe?itemId=50730&collectionId=194) in [Jawi](https://en.wikipedia.org/wiki/Jawi_alphabet) script with a smattering of English text. Ben agreed that reading order is not only important for manuscripts, but is also incredibly useful for other types of materials, especially newspapers. Cally noted that Chinese newspapers can switch line orientation on the same page from vertical to horizontal, and vice-versa. Cip underlined the use of METS for going beyond page-level encoding, and the common approach in newspapers for METS files to reference blocks within individual ALTO files. It was recognized that the tool support might be more problematic for materials like manuscripts if reading order was not encoded at the page level.

Robert confirmed that the support for reading order in PAGE-XML is very close to the proposal, though it is not necessarily clear how it should be used. There is nothing in the PAGE-XML schema to prevent sub-region elements but the tools may not currently leverage such encoding. He encouraged feedback from PAGE developers in order to facilitate transformations between PAGE-XML and ALTO, and has posted a suggestion for including a _REF_ attribute in the group elements to make the proposed changes more compatible. Robert also asked about a mechanism to document and explain the reading order convention used. Ben pointed to the use of the _Tag_ element for this purpose.

Cip enquired about blocks that don’t reference a reading order. Ben noted that his approach for viewing tools is to lay out the elements for at least one reading order by default, and to put unordered text into unordered groups. It was agreed that more examples and documentation would help clarify the best approach. 

Robert asked about the availability of ground truth for the different versions of ALTO schemas, noting that the [current repository](https://github.com/altoxml/reference_samples) has minimal examples. Ben highlighted the difficulty of contributing samples with the current structure in github, and Robert pointed out that the samples provided do not include access to the images used. One possible model for a platform is the [Living Standard approach used for hOCR](http://kba.cloud/hocr-spec/1.2/), which includes [inline examples](http://kba.cloud/hocr-spec/1.2/#baseline). As well, a suggested addition to the [Software wiki](https://github.com/altoxml/documentation/wiki/Software) is the [ocrd-page-to-alto](https://github.com/kba/page-to-alto) tool which is under active development. 

Cip agreed to consider moving the timeline up for the next meeting, given the urgency of the requested changes to the schema for ongoing work. One possibility is early in the new year and Ben will prepare some more examples. 

_wrt agenda item 4_. Upcoming Board Expirations:

A reminder to let Cip know if members wish to continue on the Board if their term expires at the end of the year.
