# 2026-04-22 ALTO Board Meeting Minutes

1. Welcome [**All**]
2. Topics to discuss:
	* In progress topics:
		* SCHEMATRON validation (https://github.com/altoxml/schema/issues/87) - a first version to be tested/evaluated
		* Make it possible to distinguish hard and soft hyphens (https://github.com/altoxml/schema/issues/86) (and related https://github.com/altoxml/schema/issues/43) - see latest comments
		* Non Linear Hyphens (https://github.com/altoxml/schema/issues/41) - how to deal with cross-page linking? 
		* Reopen xLink related topic (https://github.com/altoxml/schema/issues/67) - use case found where this is used
  		* Register alto/text as MIME type (https://github.com/altoxml/schema/issues/40)
	* Topics closed:
		* OCR correction attributes: CS, ILLS, DBTS (https://github.com/altoxml/schema/issues/21)
3. Face-to-face meeting proposal: 
    * ICDAR 2026, Vienna, Austria, 30th August - 4th September 2026
	* ICPR 2026, Lyon, France, 17th August - 22nd August 2026
4. Other business. [**All**]
	* Look for next Chair of ALTO Board
    * Stefan Boddie decided to step down from ALTO Board
	
**Attending members**
* Frederick Zarndt
* Clemens Neudecker
* Ashok Popat
* Cally Law
* Ciprian Dinu

## Meeting Context

The ALTO Board convened to discuss the development of version 5.0 of the ALTO schema, focusing on quality assurance improvements, schema cleanup, and future planning. 
## Key Discussion Topics

### 1. Schematron Validation System

Issue: https://github.com/altoxml/schema/issues/87

Ciprian presented a Schematron validation system developed in collaboration with Thomas, designed to provide quality assurance checks beyond standard XML schema validation.

#### Validation Rules proposed:

- Coordinate Validity 
    - Ensures all coordinates (position, width, height) are positive values
    - Validates that coordinates fall within page boundaries
    - Checks that all bounding boxes are contained within their parent containers
- Container Validation 
    - Verifies text lines are fully contained within text blocks
    - Ensures strings are contained within text lines
    - Validates all blocks are within the print space
    - Checks for empty containers (blocks without content)
- Reference Checking 
    - Validates that all tag references (layout, structure, named entity) point to existing IDs in the tags section
    - Prevents invalid tag references
- Overlap Detection 
    - Identifies overlapping elements within text lines and blocks
    - Implemented as warnings rather than errors
    - Plans to add tolerance thresholds for acceptable overlap
    - Future enhancement: shape-level overlap detection with stricter rules

#### Implementation Approach:

The Schematron validation is designed as a complementary tool to standard schema validation, not a replacement. It provides additional quality checks that cannot be enforced through XSD schema alone. The system uses different verbosity levels (error, warning, info) to categorize issues based on severity.

#### OCR-D PageXML Validation:

Clemens described parallel validation work in the OCR-D community using Python-based rules for PageXML. This system includes:
- Similar quality checks to proposed ALTO Schematron rules
- Automated correction utilities that fix detected errors
- Large-scale testing on millions of historical documents
- Potential for cross-pollination of validation approaches between PageXML and ALTO

#### Community Testing Plan:

- Ciprian will work with Thomas to publish the Schematron rules on GitHub with validation instructions
- Board members and community participants will test the rules on their document collections
- Clemens volunteered to run validation on 10 million historical document pages (7 million historical documents + 3 million newspapers)
- Feedback will be collected on usefulness, unexpected findings, and suggestions for additional tests
- Future tests planned: hyphenation validation, language-specific rules (e.g., Chinese character-per-word validation)

### 2. ALTO Schema Version 5.0 Changes

The board discussed breaking changes that necessitate a major version release, focusing on schema cleanup and deprecation removal.

#### Confirmed Changes:

- Accuracy Restriction: Limited to values between 0 and 100 (https://github.com/altoxml/schema/issues/89)
- Polygon Format Enforcement: Restricted to two specific formats using regular expressions (announced in 4.4, now enforced) (https://github.com/altoxml/schema/issues/80)
- Glyph Character Limit: Removed single-character restriction after discovering Hebrew and other languages require multiple Unicode characters for composed glyphs (https://github.com/altoxml/schema/issues/85)
- Reading Order Cleanup: Removal of deprecated IDNEXT attribute (replaced by ordered/unordered groups since version 4.3) (https://github.com/altoxml/schema/issues/82)
- xLink Removal: Under reconsideration after discovering valid use case (see section 4) (https://github.com/altoxml/schema/issues/67)

### 3. Hyphenation Handling

The board addressed two distinct hyphenation-related issues:

#### A. Hyphen Type Attribute (Soft vs. Hard Hyphens)

Issue: https://github.com/altoxml/schema/issues/86

Original proposal from the community requested an attribute to distinguish between soft hyphens (line-break hyphens) and hard hyphens (compound word hyphens).
Key Discussion Points:
- The same glyph can represent different hyphen types depending on context
- Different glyphs (especially in Gothic fonts) can represent the same hyphen type
- Initial concern: Adding semantic meaning conflicts with ALTO's principle of representing printed content
- Clemens argued that practical benefits outweigh philosophical concerns in this case
- Ashok agreed exceptions can be made when benefits are clear (this is one of the cases where it makes sense)

Resolution:
Ciprian will complete the original proposal and put it to vote for inclusion in ALTO 5.0. The attribute will explicitly indicate hyphen type (soft/hard) to support downstream processing and AI model training.

#### B. Non-Linear Hyphenation Across Pages

Issue: https://github.com/altoxml/schema/issues/41

This addresses complex cases where hyphenated words span across different pages or non-sequential reading areas (e.g., main content and footnotes).
Use Case Example:
A page with main content and footnotes where reading order is ambiguous — does the hyphenated word in the main content continue in the page/next content section or in a footnote?

Resolution:
- Determined to be outside ALTO's scope (similar to article structure in newspapers)
- Should be handled externally through METS hierarchical structure
- ALTO maintains page-level focus; cross-page relationships belong in container formats
- Ciprian will update the issue clarifying the scope limitation
- Cally will investigate how their newspaper digitization system handles article linkages across pages (as similar topic)

### 4. xLink Namespace Discussion

Issue: https://github.com/altoxml/schema/issues/67

The board revisited the decision to remove XLink support after discovering a legitimate use case.

#### Original Problem:

- ALTO uses xLink from Library of Congress but with W3C namespace, causing validation issues
- Similar problems exist in MODS, PREMIS and METS
- Previous discussion found no active use cases, leading to removal decision

#### Discovered Use Case:

Ciprian found examples where xLink is used to reference image snippets (illustrations, photographs) extracted as separate files from newspaper pages. The graphical elements in ALTO reference these external image files using xLink attributes.
Philosophical Debate:
Ashok raised the question of ALTO's scope: Should it represent only the physical layout and printed content, or should it include references to extracted media? This parallels the earlier hyphenation discussion about semantic vs. physical representation.
Resolution:
- Clemens argued this is a "lazy" approach — the information is already in ALTO (coordinates, layout, original full page image)
- Image snippets can be dynamically extracted using existing coordinate information
- The practical value is limited compared to the complexity of maintaining xLink
- Modern presentation systems (f.e. IIIF based on JSON manifests) handle this more elegantly
- Decision: Proceed with xLink removal as originally planned
- Clemens will write a supporting comment on the GitHub issue

### 5. Closed Issues

#### Text Legibility Attribute:

Issue: https://github.com/altoxml/schema/issues/21

Original request from National Library of France (Jean-Philippe Moreux) to add attributes indicating text legibility, correction status, or manual correction uncertainty. After consultation with BnF (Sebastien and Jean-Philippe), determined to be no longer relevant. Text correction is not a current priority, and the feature was closed.

### 6. MIME Type Registration

Issue: https://github.com/altoxml/schema/issues/45

Discussion about registering "application/alto+xml" as an official MIME type with IANA.
Context:
- Originally motivated by IIIF integration requirements
- IIIF issues have since been resolved through other means
- Registration process requires documentation and IANA proposal submission
- Moderate effort with unclear benefit-to-effort ratio

Status:
Labeled as "nice to have" rather than essential. Frederick will investigate requirements and process. Clemens noted it would provide additional legitimacy and allow differentiation from other XML-based formats (PAGE, TEI) but is not critical.

### 7. Face-to-Face Meeting Planning

#### Venue Options:


| **Conference** |  **Location**  |   **Dates**    |     **Votes**     |
|----------------|----------------|----------------|-------------------|
| ICDAR          | Vienna, Austria| Aug 30 - Sep 4 | 4 votes (leading) |
| ICPR           | Lyon, France   | Aug 17-22      | Fewer votes       |

#### ICDAR Advantages:

- More focused on document analysis and recognition
- HIP (International Workshop on Historical Document Imaging and Processing) workshop scheduled as post-conference event
- Potential external attendees: Prima group members, British Library representatives, SBB colleagues

#### ICPR Context:

Broader image processing conference, less specialized in document analysis. Ciprian noted from past experience that ICPR covers many areas beyond documents, making ICDAR more relevant for ALTO community.

#### Next Steps:

- Voting remains open until end of May for final decision
- Clemens will provide organizer contacts and explore space options
- Ciprian will coordinate logistics once attendance is confirmed
- Possibility of inviting external participants to broaden discussion

### 8. Board Leadership Transition

Ciprian announced his intention to step down as chair while remaining an active board member.

#### Rationale:

- Believes periodic rotation brings fresh perspectives and new ideas
- Suggests academic representation might balance current industrial perspective
- Feels the board has become increasingly technical, potentially limiting broader strategic thinking
- Acknowledges difficulty finding new features for version 5.0 as a sign that new leadership could help

#### Timeline and Process:

- Ciprian will continue as chair through end of 2026
- Will send email to all board members soliciting interest
- Topic will be prioritized at the top of next meeting agenda
- Board members encouraged to suggest candidates or express interest

### 9. Related Community Initiatives

#### AI4LAM Working Group:

Clemens mentioned a new working group formed by AI4LAM (AI for Libraries, Archives, Museums) focused on text recognition. The group holds monthly open meetings and may provide opportunities for ALTO community engagement and industry representation.

## Action Items Summary

### Ciprian's Actions:

1. Publish Schematron validation rules on GitHub with testing instructions
2. Complete and submit hyphen type attribute proposal for voting
3. Update cross-page hyphenation topic, explain this is outside ALTO scope
4. Send email to all board members about chair succession
5. Schedule next meeting for June 2025
6. Coordinate with Clemens on ICDAR meeting logistics if confirmed

### Clemens's Actions:

1. Compare Schematron rules with OCR-D PageXML validation coverage
2. Run Schematron validation on 10 million historical document pages
3. Write supporting comment on xLink removal GitHub issue
4. Provide ICDAR organizer contacts to Ciprian
5. Propose potential external participants for face-to-face meeting

### Cally's Actions:

1. Investigate how current newspaper digitization system handles article linkages across pages on NLB
2. Determine which ALTO elements/parameters are used for cross-page article connections
3. Report findings to the board

### Frederick's Actions:

1. Research MIME type registration requirements and process
2. Report findings at next meeting

### Community Actions:

1. All interested participants: Test Schematron rules and provide feedback
2. Board members: Consider chair position and suggest candidates

## Technical Decisions Pending Vote

1. Hyphen type attribute addition (soft/hard distinction)
2. Cross-page hyphenation scope clarification
3. IDNEXT attribute removal confirmation
4. Final decision on face-to-face meeting venue (ICDAR vs. ICPR)

## Meeting Logistics

**Next Meeting:** To be scheduled for June 2025
**Regular Schedule:** Returning to Wednesday, or Thursday at 3:30 PM Central European Time
**Note:** Stephane Bodie from New Zealand has stepped down due to scheduling difficulties with time zones
