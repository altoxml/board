# 2021-04-29 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * schema edits:
      * https://github.com/altoxml/schema/blob/831adab03d0b20d3d6a220f082ce496a18caef12/v4/alto-4-2.xsd#L728 - as per schema issue [Typo processing{,Step}Type #71](https://github.com/altoxml/schema/issues/71)
      * https://github.com/altoxml/schema/blob/831adab03d0b20d3d6a220f082ce496a18caef12/v4/alto-4-2.xsd#L1047 - correction?
      * https://github.com/altoxml/schema/blob/831adab03d0b20d3d6a220f082ce496a18caef12/v4/alto-4-2.xsd#L525 - as per _CC_ discussion at [2021-02-25 Board Meeting](https://github.com/altoxml/board/blob/gh-pages/minutes/2021/2021-02-25%20ALTO%20Board%20Meeting%20Minutes.md)
      ```xml
      <xsd:documentation>Deprecated. Where possible, the Gylph element should be used instead with the associated and more precise GC and VC attributes.</xsd:documentation>
      ```
   * new:
      * [Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions. #67](https://github.com/altoxml/schema/issues/67) - current use in [4.2 schema](https://github.com/altoxml/schema/blob/831adab03d0b20d3d6a220f082ce496a18caef12/v4/alto-4-2.xsd#L443) and possible modification based on [Premis-v3-0](https://github.com/LibraryOfCongress/premis-v3-0/blob/master/xsd#L41) and [METS](https://github.com/mets/METS-schema/blob/noxlink/mets.xsd#L1853)
      * [Support for script in addition to language #70](https://github.com/altoxml/schema/issues/70)
   * high priority:
      * [ALTO - PAGE xml: Object mapping and possible transformation generation #48](https://github.com/altoxml/schema/issues/48) - has this [been addressed](https://github.com/PRImA-Research-Lab/prima-page-converter)?
      * [ALTO & IIIF integration #45](https://github.com/altoxml/schema/issues/45) - feedback from [IIIF Text Granularity Technical Specification Group](https://iiif.io/community/groups/text-granularity/)
      * [Reading Order (IMPACT) #18](https://github.com/altoxml/schema/issues/18) - possible synergy with [Clarify implicit reading order #68](https://github.com/altoxml/schema/issues/68) and [Confidence value for Layout detection of elements #69](https://github.com/altoxml/schema/issues/69)?
      * [ALTO support for encoding OCR segmentation ambiguity #63](https://github.com/altoxml/schema/issues/63)
      * [Confidence value calculation (CC - WC - PC) - annotation extension #23](https://github.com/altoxml/schema/issues/23)
   * full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. Preliminary findings from paper for the [2021 ICDAR conference](https://icdar2021.org/) on inconsistencies in accuracy use between characters and words. [**Clemens**] 
5. Board membership:
   * Candidate nomination from KB
   * Chair position available
6. Other business. [**All**]

**Attending members**
* Art Rhyno
* Clemens Neudecker
* Frederick Zarndt
* Hany A. Abdellatif
* Jean-Philippe Moreux
* Nate Trail
* Raju Buddharaju
* Sébastien Cretin
* Stefan Pletschacher

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * schema edits:
      * https://github.com/altoxml/schema/blob/831adab03d0b20d3d6a220f082ce496a18caef12/v4/alto-4-2.xsd#L728 - as per schema issue [Typo processing{,Step}Type #71](https://github.com/altoxml/schema/issues/71) - there was general agreement that this was a typo in the schema and can be corrected in the next version. Art will confirm with Cip.
      * https://github.com/altoxml/schema/blob/831adab03d0b20d3d6a220f082ce496a18caef12/v4/alto-4-2.xsd#L1047 - "variant" in first line of _documentation_ should be "glyph", this is also a small mistake in the schema and will be fixed in the next version.
      * https://github.com/altoxml/schema/blob/831adab03d0b20d3d6a220f082ce496a18caef12/v4/alto-4-2.xsd#L525 - the use of _CC_ will be marked as deprecated in the documentation, and will be reflected in a github issue.
   * new:
      * [Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions. #67](https://github.com/altoxml/schema/issues/67) - the approach used in [Premis](https://github.com/LibraryOfCongress/premis-v3-0/blob/master/xsd#L41) will be proposed in a github issue.
      * [Support for script in addition to language #70](https://github.com/altoxml/schema/issues/70) - Clemens noted that this issue originated in PAGE to ALTO mapping work. Ashok flagged the use of [BCP 47](https://en.wikipedia.org/wiki/IETF_language_tag) at Google, which combines subtags from other standards. Art will add a link to the issue.
   * high priority:
      * [ALTO - PAGE xml: Object mapping and possible transformation generation #48](https://github.com/altoxml/schema/issues/48) - [OCR-D](https://ocr-d.de/en/about) has been pursuing a feature complete transformation and Clemens pointed to the the [associated issue](https://github.com/kba/page-to-alto/) which identifies areas which still need attention. Stefan noted that the [PRImA project's tool](https://github.com/PRImA-Research-Lab/prima-page-converter) has received a lot of use and that it would be helpful to have a structured document that identifies any gaps that still exist.
      * [ALTO & IIIF integration #45](https://github.com/altoxml/schema/issues/45) - the feedback from the [IIIF Text Granularity Technical Specification Group](https://iiif.io/community/groups/text-granularity/) suggests that this issue could be de-escalated since ALTO is included in the [Text Granularity Extension](https://iiif.io/api/extension/text-granularity/). Frederick asked about examples that might be available at this point for the use of ALTO with IIIF. There is a sense that these are in the pipeline, in particular, as a result of transcription projects, and this issue will be kept open in order to keep the links and associated documentation attached to it accessible.
      * [Reading Order (IMPACT) #18](https://github.com/altoxml/schema/issues/18) - Stefan described how the issue has its roots in the [IMPACT project](https://www.primaresearch.org/projects/impact) going back to 2008, and in the ambiguity of the starting point for the _IDNEXT_ attribute, suggesting that the mechanisms in [PAGE-XML](https://github.com/PRImA-Research-Lab/PAGE-XML) could be replicated. Clemens underlined how useful reading order has become for activities like text generation for data mining and for other uses in the Digital Humanities. The high priority status will be moved to [Clarify implicit reading order #68](https://github.com/altoxml/schema/issues/68). 
      * [ALTO support for encoding OCR segmentation ambiguity #63](https://github.com/altoxml/schema/issues/63) - Art has been in touch with the proposal's author, who is working through some feedback from the [Transkibus](https://readcoop.eu/transkribus/) project and others, and hopes to schedule a special meeting on this topic.
      * [Confidence value calculation (CC - WC - PC) - annotation extension #23](https://github.com/altoxml/schema/issues/23) - this is still an area of active interest and will remain high priority.

_wrt agenda item 4_. Preliminary findings from paper on inconsistencies in accuracy use between characters and words.

Clemens gave a sneak preview of the work that his team has been doing for the [HIP workshop](https://blog.sbb.berlin/hip2021/), which is co-located with the ICDAR conference this year in Lausanne, Switzerland. He reminded the Board that there are still 2 weeks to submit a paper to HIP, and that there are plans for possible onsite participation. Clemens described the many challenges to evaluating OCR accuracy. There are too many documents to rely solely on ground truth, but sampling techniques tend to ignore layout analysis. For users interested in using OCR documents for advanced processing, like natural language or distant reading, it is essential to retain the correct sequence for paragraphs, columns, etc. Most of the common metrics do not address this.

The team did some comparisons with many of the common tools, including those from IMPACT, the [PRImA evaluation tools](https://www.primaresearch.org/tools/PerformanceEvaluation) and the [dinglehopper](https://github.com/qurator-spk/dinglehopper) tool from the [Qurator](https://qurator.ai/) project. The comparisons were carried out on two datasets, one dataset consisted of historical books and the other consisted of newspapers. Even with the same measures, for example, word error rate, the tools provided results that differed substantially. This could be due to implementation details or lack of specification, for example, how to treat ligatures, or how to combine code points. Clemens also noted differences in alignment between the ground truth and the OCR results, and the sometimes inconsistent treatment of different languages by the same tool.

ALTO could have role in clarifying some of the varied aspects of OCR, such as code points for characters and the use of spaces. Consistent metrics for layout analysis are also needed, PRImA, in particular, has done good work on this but there is still a lack of standardization that needs to be addressed. Clemens hopes the paper will be finished soon and can share a copy when it is completed.

Art asked about the extent to which OCR quality impacts downstream analysis in areas such as name entity recognition. Clemens suggested that there usually needs to be an evaluation phase for text analysis projects to help measure the appropriateness of the OCR for the task.  Kudos were given to the [IMPACT Historical Document Images](https://www.primaresearch.org/www/assets/papers/HIP2013_Papadopoulos_Dataset.pdf) dataset and the [ENP Image and Ground Truth Dataset of
Historical Newspapers](https://www.primaresearch.org/www/assets/papers/ICDAR2015_Clausner_ENPDataset.pdf), which include reading order. Stefan noted the difficulty of using OCR metrics with funding agencies and other types of decision-makers, where there is a desire to see one number for use in evaluation, a point echoed by Clemens where applications for funding sometimes require an internal OCR accuracy rate to be provided. Frederick asked how the results of this work could be used in the future. The importance of providing the underlying data and the abilty to reproduce results was emphasised, and the identification of areas for further research is a key direction, for example, defining better metrics within OCR projects. Clemens flagged the work by David Smith and others in the [Research Agenda for Historical and Multilingual OCR](https://repository.library.northeastern.edu/collections/neu:cj82sz060) report, which includes a recommendation for better measures to reflect use cases from the DH community. Clemens also underlined the need for cultural heritage organizations to provide transparent information on the quality of the OCR results used in services and projects in order to allow informed decisions by users.

Frederick raised the use of accuracy metrics for open and commercial OCR engines, would it be possible for OCR systems and services to use common metrics to support better comparison points in selecting OCR options? There was general agreement that better metrics would help everyone involved in OCR provision and use. Frederick described a use case involving [Ancient Greek](https://en.wikipedia.org/wiki/Greek_diacritics), where challenges in provisioning solutions for a non-mainstream language in terms of OCR might also provide a sandbox for defining accuracy. 

_wrt agenda item 5_. Board membership

Evelien has identified someone at the [Koninklijke Bibliotheek](https://www.kb.nl) who could step into her spot on the Board and Art will send out a CV for the candidate. Art also reminded the Board that the Chair position will be available in January, 2022, and encouraged anyone interested to contact him. 

_wrt agenda item 6_. Other business:

Clemens provided a link to a [background document](https://www.degruyter.com/document/doi/10.1515/abitech-2015-0014/html) to give some sense of the type of OCR metrics used in Germany for funding. Ashok and others expressed support for the prospect of meeting face-to-face at ICDAR, and Stefan noted that conference funding and procedures may take some time to stabilize as conferences start to offer in-person registration again.

The next Board meeting will likely be held in June.
