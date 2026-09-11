# 2026-08-31 ALTO Board Meeting Minutes

1. Welcome [**All**]
2. Topics to discuss:
  * Collect new ideas feedback from external users
  * SCHEMATRON validation (https://github.com/altoxml/schema/issues/87) - feedback from members that already tested the available schema
  * ALTO documentation:
    * Is needed?
    * What to contain, how to be structured?
    * Unify/clean all different incomplete existing documentation (on LOC official web page, on github, other)
    * Collect images that can be used as samples (out of copyright)
    * Prepare a web page for this purpose to be accessed from LOC official page
3. Organisatoric topics:
  * The list of active Board members was reduced in the last period of time
  * Propose new candidates to join the board
	
**Attending members**
* Sebastien Cretin
* Ashok Popat
* Hany Abdellatif
* Ciprian Dinu
* Clemens Neudecker
* Cally Law

**External**
  
* Henry Rowley (Google)
* Gerald Schreiber (CCS)

## Key Takeaways

- The ALTO board discussed the need to improve documentation, consolidate it into a single location (GitHub), and create an "ALTO cookbook" with use cases and examples.
- PageXML vs. ALTO was debated; ALTO is seen as more sustainable for cultural heritage institutions, and the feature gap between the two has narrowed significantly.
- Adoption of newer ALTO versions (3.x, 4.x) remains low; many tools and institutions still use version 2.x.
- ALTO version 5.0 is technically ready for release; the board agreed to tie the release to completion of improved documentation.
- The use of AI/LLMs for document processing, newspaper digitization challenges, and coordinate output from multimodal models were discussed.
- A board recruitment round was proposed to increase the number of active contributors.
- Schematron validation tooling was discussed as a complementary quality-assurance mechanism for ALTO files.

---

## Discussed Topics

### 1. Introductions and Meeting Setup

Ciprian welcomed attendees and introduced the agenda, inviting fresh perspectives from participants not regularly involved in board work.

- **Details**
    - Ciprian: Welcomed all participants and noted the goal of gathering new ideas from people outside the day-to-day board activities.
    - Henry Rowley: Introduced himself as a newcomer, noting his background in handwritten text recognition (HTR) over several years, recently having switched topics.
    - Ashok: Noted that Henry's expertise in HTR could be highly valuable given ALTO's growing relevance to handwriting recognition.
- **Conclusion**
    - The meeting aimed to gather fresh input on ALTO's direction, particularly regarding HTR and handwriting support, but not only.

---

### 2. PageXML vs. ALTO: Sustainability and Feature Parity

The group discussed the relative merits of PageXML and ALTO, particularly in the context of cultural heritage institutions and HTR workflows.

- **Details**
    - Clemens: Noted that PageXML is widely used in the library/archive/museum domain for HTR encoding, but its maintenance and development are limited. The lead developer lacks resources to continue development and has shifted focus.
    - Clemens: Highlighted that ALTO, backed by an organized board, is more sustainable from a long-term institutional perspective.
    - Clemens: Suggested exploring what features ALTO could add or highlight to position itself as a better alternative to PageXML for HTR use cases.
    - Clemens: Mentioned that the feature gap between PageXML and ALTO has narrowed considerably; only a few features still give PageXML dominance for handwriting (e.g., certain training data storage conventions).
    - Ciprian: Noted that baselines in ALTO were previously just straight-line coordinates but are now supported as polygonal lines (since version 4.2), aligning more closely with PageXML capabilities.
    - Ciprian: Mentioned that ALTO now has an improved reading order concept superseding the old ID-next approach.
    - Ciprian: Pointed out that PageXML is often used for storing training data and editing text, while ALTO serves a different purpose — representing the page with full structural detail for presentation and indexing.
    - Clemens: Suggested identifying the specific features that currently give PageXML dominance in handwriting contexts, to determine whether ALTO can address them.
- **Conclusion**
    - ALTO is considered more sustainable than PageXML for long-term institutional use.
    - The feature gap has narrowed; targeted improvements could make ALTO a viable alternative for HTR workflows.
    - A one-to-one conversion between PageXML and ALTO is not straightforward due to differing purposes.

---

### 3. Low Adoption of Newer ALTO Versions

The group discussed the persistent use of older ALTO versions (primarily version 2.x) by many tools and institutions.

- **Details**
    - Clemens: Reported difficulty with the German Digital Library, which only supports ALTO version 2.x, despite newer versions being available.
    - Clemens: Noted that most tools, except those maintained by the board itself, do not support up-to-date ALTO versions.
    - Clemens: Suggested that broader adoption of newer versions could be incentivized by expanding ALTO's applicability to handwriting recognition use cases.
    - Ciprian: Mentioned that BNL uses version 4.4, but most institutions remain on version 2.x (for example NDNP specification broadly used in USA requests 2.0) or 3.x.
    - Hany: Noted that National Qatar Library had moved from hOCR to ALTO for sustainability and synergy reasons and is currently converting its entire collection.
- **Conclusion**
    - There is a significant gap between available ALTO versions and actual adoption in the field.
    - Incentives and demonstrators are needed to encourage uptake of newer versions.

---

### 4. ALTO Dialects and Non-Standard Extensions

The group discussed the existence of custom ALTO dialects (e.g., from Transkribus and BNF) and how to handle them.

- **Details**
    - Clemens: Noted that Transkribus exports a custom ALTO variant with non-standard extensions, requiring correction before validation.
    - Ciprian/Sebastien: Identified on old documentation a BNF-specific ALTO dialect, documented in French, involving minor differences (mainly around document IDs and header metadata).
    - Ciprian: Proposed creating a central registry of known ALTO dialects, similar to METS profiles, to document their differences from the main schema.
    - Ashok: Suggested that if Transkribus extensions are primarily metadata rather than structural changes, they could be more easily incorporated into the standard.
    - Ashok: Emphasized that the goal should be consolidation, not encouragement of further dialect proliferation.
- **Conclusion**
    - A central overview of ALTO dialects should be created and maintained by the board.
    - The board should aim to incorporate useful extensions from dialects (e.g., Transkribus) into the official standard where appropriate.
    - New dialects should not be encouraged.

---

### 5. Semantic Structuring, TEI Export, and Layering in ALTO

The group discussed user demand for semantic structuring in ALTO and the challenge of converting ALTO to TEI.

- **Details**
    - Clemens: Noted ongoing requests from users for TEI export with semantic structuring (e.g., captions, headings, chapter titles).
    - Clemens: Described the challenge of generating useful TEI from ALTO without introducing semantics directly into ALTO, proposing rule-based and NLP/LLM-assisted conversion approaches.
    - Clemens: Gave the example of image captions: using geometric proximity and semantic analysis to label a text block as a caption in TEI.
    - Ciprian: Referenced the tags concept introduced in ALTO version 2.1, which allows semantic markup (named entities, layout tags, structure tags) to be added non-intrusively, always referencing tags from regions by ID.
    - Ciprian: Noted that the structure tags referencing mechanism in ALTO is theoretically powerful but rarely used in practice, as most users prefer METS for logical structure.
    - Sebastien: Mentioned that BNF has over 1 million ALTO files with rich semantic information in the tags section (titles, subtitles) generated since 2016.
    - Clemens: Noted that the tags section works well for structure that does not span across pages.
    - Ciprian: Outline the possibility of embedding external XML vocabularies (MathML, MusicML, chemical formulas) within ALTO's "other" tag category for specialized content types.
    - Ashok: Proposed thinking about ALTO in terms of an information pipeline — from pixels to symbolic representation — where ALTO captures all essential information so downstream users do not need to return to the pixel array for semantic interpretation.
    - Clemens: Agreed with the layering concept and noted it is agnostic to the type of semantic information added.
- **Conclusion**
    - ALTO's existing layering and tagging mechanisms already support many semantic use cases, but this is not widely known.
    - Good demonstrators and documentation of these features are needed.
    - Embedding external XML vocabularies (MathML, MusicML, etc.) within ALTO is already possible and should be better documented.

---

### 6. Documentation: Current State and Improvement Plan

The group identified documentation as a critical gap and discussed how to address it.

- **Details**
    - Ciprian: Noted that existing documentation is fragmented across the Library of Congress website, GitHub (Markdown, PDFs, wikis), and other locations, with some stopping at version 2.0.
    - Clemens: Proposed consolidating all documentation into a single GitHub repository in Markdown format, with a link from the LOC page.
    - Clemens: Suggested creating an "ALTO cookbook" with chapters covering version changes, use cases, semantic layers, and practical examples.
    - Ciprian: Proposed using AI tools to generate initial documentation from the schema and comments, then refining with use-case-driven examples.
    - Ashok: Suggested that users will likely feed documentation into AI tools to ask questions, so documentation should be structured with this in mind; samples and use-case-driven content are especially important.
    - Ciprian: Proposed collecting real user questions and use cases as the basis for documentation examples.
    - Ashok: Raised the copyright challenge of using real document images as examples, suggesting generative AI could produce equivalent synthetic examples to avoid copyright issues.
    - Ciprian: Proposed a two-step approach: (1) generate generic documentation from the schema using AI, and (2) collect use cases and create representative examples.
    - Clemens: Suggested Markdown as the preferred format for machine readability and AI compatibility.
    - Ciprian: Proposed that the board review and approve documentation plan at a subsequent meeting.
- **Conclusion**
    - Documentation consolidation is a priority and will be pursued before the ALTO 5.0 release.
    - A GitHub-based, Markdown-formatted "ALTO cookbook" is the target format.
    - Use-case-driven examples, potentially generated with AI assistance, will be developed.
    - Board members will divide documentation tasks and review contributions collaboratively.

---

### 7. ALTO Version 5.0 Release Readiness

The group reviewed the status of ALTO version 5.0 and discussed the timing of its release.

- **Details**
    - Ciprian: Confirmed that version 5.0 is technically prepared, with all proposed changes implemented in separate branches and most items already voted on.
    - Clemens: Noted that the main changes involve breaking backward compatibility (e.g., removing ID-next definitions, removing xRef usage), which justifies a new major version.
    - Clemens: Expressed hesitation about releasing without improved documentation, as the new version would otherwise not be well understood or adopted.
    - Clemens: Proposed tying the release to the completion of documentation improvements.
    - Ciprian: Noted that Schematron validation is a new addition that could be included in or alongside version 5.0.
    - Ciprian/Clemens: Suggested using the release as a momentum-building opportunity, combined with a board recruitment round.
- **Conclusion**
    - ALTO 5.0 is technically ready but will be held until documentation is sufficiently improved.
    - The release decision will be revisited at the next board meeting.
    - Schematron inclusion in the release will be decided separately.

---

### 8. AI and Multimodal Models for Document Processing

The group discussed the role of AI/LLMs in document recognition, coordinate output, and newspaper processing.

- **Details**
    - Clemens: Noted that many commercial AI tools marketed as document recognition solutions do not output pixel coordinates, which are essential for library users who need to link back to scanned images.
    - Sebastien: Mentioned that the latest Mistral model outputs coordinates in JSON format, though a verification step is needed for reliability.
    - Clemens: Noted that multimodal LLMs perform well on contemporary documents and simple layouts but struggle with complex historical newspapers (multiple columns, varied fonts, overlapping elements, high information density).
    - Gerald: Described experiments where asking ChatGPT or Gemini to transcribe only article titles from a complex newspaper page yields near-perfect results, but full-page transcription fails.
    - Ciprian: Described a graph neural network approach using coordinates, text, and layout element types to group newspaper content into articles, with geometry being the dominant signal.
    - Ciprian: Noted that text content provides marginal improvement over geometry alone, except for cross-column and cross-page article continuation.
    - Ashok: Proposed the concept of ALTO as a compressed symbolic representation of the original document that could condition an LLM for mask prediction, potentially enabling efficient storage and reconstruction of page information.
    - Clemens: Acknowledged the elegance of the idea but noted that scholars often need to return to the original pixels for materiality studies (paper grain, handwriting, physical condition).
- **Conclusion**
    - Coordinates output from AI models remains a gap.
    - Complex historical newspapers remain a significant challenge for current LLMs.
    - The link between ALTO and pixel-level information remains important for scholarly use cases.

---

### 9. Newspaper Digitization: Scale, Quality, and Community

The group discussed the state of newspaper digitization globally and the communities working in this space.

- **Details**
    - Clemens: Noted that reprocessing previously digitized newspapers with modern OCR yields dramatic quality improvements (e.g., character error rates dropping from 20–30% to 1–2%).
    - Clemens: Mentioned that much German newspaper digitization is done from microfilm rather than original paper, which affects quality.
    - Clemens: Noted that article-level segmentation has historically not been done systematically in Germany and other countries.
    - Clemens: Described a project building a unified multilingual (German, Chinese, Russian) newspaper research interface using LLMs for summarization and translation, requiring article-level segmentation.
    - Hany: Mentioned work with the Qatari Football Association Archive on Arabic newspaper article extraction.
    - Cally: Confirmed that the IFLA News Media section is still operational, recently held a satellite event in South Korea, and suggested Frederick as a contact for the newspaper subgroup.
    - Clemens: Referenced the Europeana Newspapers project as a past European-scale effort that has since shifted focus away from aggregation.
    - Ashok: Estimated that newspaper digitization globally is far from complete (e.g., Japan would need 400 years at the current pace).
- **Conclusion**
    - Significant opportunities remain in newspaper digitization, article segmentation, and multilingual access.
    - The IFLA News Media section remains an active forum for this community.
    - Reprocessing existing scans with modern tools offers substantial quality gains.

---

### 10. Schematron Validation for ALTO

The group briefly discussed the Schematron-based validation tool developed for ALTO.

- **Details**
    - Ciprian: Noted that a Schematron ruleset has been published and is available for use, generating validation reports directly from ALTO files.
    - Ciprian: Mentioned that the tool currently checks rectangular bounding boxes for consistency (e.g., negative coordinates, coordinates outside page bounds) and that polygon-level checks are under consideration.
    - Ciprian: Noted that some checks are implemented as warnings rather than errors (e.g., minor coordinate overflows).
    - Clemens: Mentioned that he had planned to run the Schematron tool against a corpus of 5 million pages, but this has been delayed.
    - Clemens: Noted that OCRD has similar internal consistency checks that could be aligned with the Schematron work.
- **Conclusion**
    - Schematron validation is a useful addition to the ALTO ecosystem and will be considered for inclusion in the version 5.0 release.
    - Further testing on large corpora is planned.

---

### 11. Board Membership and Recruitment

The group discussed the need to expand the active membership of the ALTO board.

- **Details**
    - Ciprian: Noted that the active board is currently small and expressed a desire to grow it.
    - Ciprian: Invited suggestions for institutions or individuals who should be represented on the board.
    - Clemens: Proposed using the ALTO 5.0 release as a momentum-building opportunity to attract new board members.
- **Conclusion**
    - A recruitment round will be initiated to expand the active board.
    - Board members are asked to suggest candidates from relevant institutions.

---

## Challenges

- **Low adoption of newer ALTO versions**: Most tools and institutions remain on version 2.x, limiting the impact of improvements made in versions 3.x, 4.x, and 5.x.
- **Fragmented and outdated documentation**: Documentation is scattered across multiple locations, partially outdated, and not easily discoverable by new users or adopters.
- **Copyright concerns for documentation examples**: Using real document images as examples raises complex copyright issues across jurisdictions.
- **Article-level segmentation for newspapers**: Reliable, generalizable article segmentation across languages, scripts, and complex layouts remains technically difficult.
- **Coordinates output from AI models**: Most commercial and open-weight multimodal models do not output pixel coordinates, limiting their utility for library and archival use cases.
- **Small active board**: The limited number of active contributors constrains the board's capacity to execute on documentation, development, and outreach tasks.

---

## Action Items

- **Ciprian**
    - Create GitHub topics to collect ALTO use cases and user questions as the basis for documentation examples (before next meeting).
    - Initiate a board recruitment round; contact suggested candidates.
    - Coordinate the documentation task division among volunteers via email before the next meeting.
- **All board members**
    - Suggest candidates for board membership from relevant institutions.
    - Review and approve documentation contributions at the next or subsequent board meeting.
    - Share known ALTO dialects (beyond Transkribus and BNF) with the group for the dialect registry.
	- Commit hours to drafting and reviewing ALTO documentation, including generating initial content from the schema using AI tools.
    - Run the Schematron validation tool against different data corpus and provide feedback (how useful it is, what other tests to add, etc.)
- **Cally**
    - Follow up with Frederick regarding the IFLA News Media section and newspaper community contacts (no specific deadline mentioned).

