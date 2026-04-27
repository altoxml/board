# 2026-02-05 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Topics to discuss:
	* In progress topics:
		* Make it possible to distinguish hard and soft hyphens (https://github.com/altoxml/schema/issues/86) (and related https://github.com/altoxml/schema/issues/43) - see latest comments
	* Topics to discuss (older topics revisited, try to close):
		* OCR correction attributes: CS, ILLS, DBTS (https://github.com/altoxml/schema/issues/21)
		* Recommendation for link to ALTO in iiif manifest and other related to IIIF (https://github.com/altoxml/schema/issues/40, https://github.com/altoxml/schema/issues/31, https://github.com/altoxml/schema/issues/45) - review status (close/check what is still to be done)
		* Non Linear Hyphens (https://github.com/altoxml/schema/issues/41) - review status (close/check what is still to be done)
	* Release 5.0 including features on "6 - voting" status
3. Face-to-face meeting proposal: 
    * ICDAR 2026, Vienna, Austria, 30th August - 4th September 2026
4. Other business. [**All**]
	* Look for next Chair of ALTO Board

**Attending members**
* Frederick Zarndt
* Stefan Pletschacher
* John Loitzenbauer
* Hany Abdel Hamid Elsawy
* Ciprian Dinu

### Key Decisions Made

- **Hyphenation Handling:** Will be put back to a board-wide vote to decide between three approaches (add hard/soft hyphen attribute, general hyphen type attribute, or use existing content attribute) (https://github.com/altoxml/schema/issues/86 and older https://github.com/altoxml/schema/issues/43)
- **BNF Correction Attributes:** Postponed pending input from Sebastian (BNF) with example ALTO files (https://github.com/altoxml/schema/issues/21)
- **IIIF Integration:** Confirmed as functional; Frederick to investigate MIME type registration requirements (https://github.com/altoxml/schema/issues/40, https://github.com/altoxml/schema/issues/31, https://github.com/altoxml/schema/issues/45)
- **Reading Order:** Needs further work for cross-page references and IDNEXT attribute redefinition (currently proposed to be deleted in https://github.com/altoxml/schema/issues/82; discussion should be reopened and see if IDNEXT attribute can solve cases like in https://github.com/altoxml/schema/issues/41)
- **Version 5.0:** Schematron schema identified as the most compelling new feature to justify release

## Discussion Details

### 1. Hyphenation Representation in ALTO

**Issue link:** https://github.com/altoxml/schema/issues/21
**Context:** The board discussed how to distinguish between hard hyphens (part of the word, like "co-ordinate") and soft hyphens (line-break indicators) in ALTO files.
#### Three Proposals Considered

1. **Add specific attribute:** Create a dedicated attribute to mark hard vs. soft hyphens
2. **General hyphen type:** Implement a more flexible hyphen type attribute (though additional use cases beyond hard/soft were unclear)
3. **Use existing content attribute:** Rely on the content attribute to indicate hyphen type (most board members initially favored this, but may not be the correct solution - see comments from topic on github)
#### Key Discussion Points

- **Original concern:** The topic originator argued that graphical representation (what appears in the scan) should be distinguished from semantic meaning (what the hyphen actually represents)
- **Stefan's broader observation:** This issue extends beyond hyphens to other characters where graphical representation may hide different meanings: 
    - Different types of whitespace (spaces vs. tabs vs. non-breaking spaces)
    - Bullet points vs. dashes at line beginnings
    - Different hyphen glyphs in Gothic/Fraktur materials
- **Language considerations:** Frederick raised the question of how non-Latin scripts handle hyphenation. Hany confirmed Arabic does not use hyphens for word splitting

**Resolution:** Ciprian will post the topic for further comments and call for a board-wide vote on the best solution. The decision will determine whether ALTO schema changes are needed or if the current content attribute approach is sufficient. 
### 2. Additional OCR Correction Attributes (BNF Proposal)

**Issue link:** https://github.com/altoxml/schema/issues/21
**Background:** An old proposal (12 years) from BNF suggested adding attributes beyond the existing "corrected string" flag to capture more nuanced correction information, such as "illegible text" or "correction uncertainty."
#### Discussion Points

- **Scope concern:** Ciprian questioned whether these additions move ALTO beyond its core purpose of representing scanned material transcription into the realm of corrected/edited documents
- **Practical usage:** BNF reportedly uses a derived ALTO schema with additional statistics at the file header level (e.g., illegible character counts, character exceptions)
- **Stefan's pragmatic view:** The lack of complaints over 12 years suggests low urgency; topic could be closed and reopened if needed

**Decision:** Postponed until Sebastian from BNF can join a meeting to explain their use case in detail and provide example ALTO files showing their current implementation. 
### 3. IIIF Integration and MIME Type Registration

**Issue link:** https://github.com/altoxml/schema/issues/31, https://github.com/altoxml/schema/issues/45, https://github.com/altoxml/schema/issues/40
**Current Status:** ALTO files can now be directly linked in IIIF manifests, making the integration functional. The question remains whether formal MIME type registration is necessary.

#### MIME Type Registration Discussion

- **Proposed format:** application/alto+xml (similar to application/tei+xml for TEI format)
- **Alternative approach:** Use text/xml with profile parameter specifying ALTO schema and version
- **Stefan's analysis:**
    - Registration would be "proper" and reserve the type name
    - No fees involved, but requires formal application and specification submission to IANA
    - Limited practical value unless tools actually support the MIME type
    - Needs a "champion" willing to invest substantial time in the process
- **Frederick's offer:** As a IIIF ambassador, he volunteered to investigate registration requirements and report back
#### IIIF Conference Opportunity

The annual IIIF conference is scheduled for June 1-3 in Amsterdam. 

**Decision:** Create a new status label for topics that are "nice-to-have" but lack urgency or a champion. Frederick will investigate MIME type registration requirements as a first step. 

**Action:** Ciprian create status label and assign it to specific topics

### 4. Cross-Page References and Reading Order

**Issue link:** https://github.com/altoxml/schema/issues/41
**Problem Identified:** The board examined a specific case where a hyphenated word at the end of a page incorrectly appeared to link to a word on the next page, when actually both were part of a footnote continuing across pages.

#### Technical Challenges

- **Current limitation:** ALTO schema allows multiple pages per file, but in practice, nearly all implementations use one page per ALTO file
- **Reading order scope:** Current reading order structures work well within a single page but don't address cross-page or cross-file references
- **IDNEXT attribute:** Previously proposed for removal (as part of v5.0 cleanup), but this use case suggests it may still be needed
- **Conflict with unordered groups:** If IDNEXT is retained, its interaction with ordered/unordered groups needs clarification

#### Stefan's Broader Perspective

This is fundamentally a reading order problem, not unique to hyphens. Similar issues arise with:
- Footnotes that continue across pages
- Drop capitals that are separate from but part of the text flow
- Inserted materials (e.g., maps in books) that interrupt the normal reading sequence
- Advertisements in magazines that exist "in parallel" rather than in true sequence

#### Possible Solutions Discussed

- **Continuation attribute:** PAGE XML has a boolean "continuation" attribute indicating blocks that continue from previous columns/pages—unclear if ALTO adopted this
- **URI references:** Using URIs with fragment identifiers could enable cross-file references
- **Group-level linking:** Instead of block-level IDNEXT, implement continuation at the group level
- **Alternative reading orders:** Support multiple reading paths (e.g., read footnote immediately vs. continue main text)

**Outcome:** Ciprian will review the reading order and IDNEXT functionality in detail, particularly regarding cross-page and cross-file references. The IDNEXT removal proposal for v5.0 may need to be reconsidered or redefined to work with ordered/unordered groups. 

### 5. Version 5.0 Planning and Features

**Release Context:** The last ALTO version was released almost 2 years ago. Version 5.0 is planned as a major release with breaking changes focused on cleanup, but lacks compelling new features.
#### Proposed Breaking Changes


|                      **Change**                      |                                     **Rationale**                                      |                    **Impact**                     |
|------------------------------------------------------|----------------------------------------------------------------------------------------|---------------------------------------------------|
| Limit accuracy attribute to 0-100 range              | Consistency with other similar attributes                                              | Previously unrestricted values become invalid     |
| Remove single-character restriction on glyph content | Some languages (e.g., Hebrew) require multi-character representation for single glyphs | Enables proper support for composed characters    |
| Standardize polygon point format                     | Too many format variations (spaces, commas, brackets) complicate processing            | Custom polygon formats become invalid             |
| Remove deprecated reading order attributes           | New reading order structure in v4.3 makes old attributes redundant                     | Old reading order definitions no longer supported |
| Remove xLlink usage                                  | No known usage in practice; only available in text blocks                              | xLink references become invalid                   |

#### Potential New Features Proposed and Discussed in the last period

- **Schematron schema (most promising):**
    - Enables validation beyond what XSD can express (e.g., box containment rules, coordinate ranges)
    - Can enforce language-specific rules (e.g., Chinese words must be single characters)
    - Thomas from National Library of Netherlands is developing a first version
    - Will be distributed to board members for testing before inclusion
    - Frederick suggested adding this to v5.0 as a compelling new feature
- **Relations between ALTO components:**
    - Link footnotes to their reference points in main text
    - Express key-value pairs (useful for invoices, forms)
    - Define parent-child relations beyond default page→block→line→string hierarchy
    - Status: Proposal exists but limited activity
- **Embedded specialized schemas:**
    - Allow insertion of MathML for mathematical formulas
    - Support music notation schemas for musical scores
    - Enable technical diagram schemas for engineering documents
	- Any other specific description for non regular text elements (like formula, drawings, musical scores, etc)
    - May already be possible using existing "Tags"/"OtherTags" functionality—needs documentation/examples
- **Handwritten text support improvements:**
    - Allow text content at line or block level (not just string level)
    - Better suited for handwriting where line boundaries are less defined
    - Concerns about content consistency between levels
    - Consensus leaned toward detailed page representation over simplified training data
	
**Decision:** Frederick suggested releasing v5.0 with the Schematron schema as the primary new feature, once it's been tested by the board. This would provide both cleanup (breaking changes) and a valuable new capability (advanced validation). 

### 6. Board Leadership and Membership Updates

**Leadership Transition:** Ciprian announced his intention to step down as chair after serving for approximately 4 years.
#### Ciprian's Reasoning

- Desire for fresh perspectives and new ideas
- Preference for someone from the academic/research world rather than industry
- Belief that academic perspective brings more thorough analysis vs. industry focus on quick solutions
- Will send detailed email to board inviting expressions of interest
#### Potential Candidates Discussed

- **Yves Maurer (Luxembourg):** Frederick suggested inviting him to join the board and potentially lead

#### Board Membership Updates Needed

Frederick noted the Library of Congress board member list might be outdated. A review may be required:

#### New Board Members Recently Added

- Gregor Lantzinger (Transkribus)
- Stefan Boddie (Veridian)
  
**Action:** Ciprian will update the ALTO Editorial Board membership list and send an email announcing his intention to step down, inviting expressions of interest for both the chair position and board membership, with consideration for inviting Eve Maurer and others. 

### 7. Face-to-Face Meeting Planning

The board discussed the need for an in-person meeting, which hasn't occurred in almost 3 years (last face-to-face was 2023).
#### Proposed Venues

- **ICDAR Conference:** Vienna, Austria (Ciprian's primary suggestion)
- **ICPR Conference:** France (alternative option)
- **IIIF Annual Conference:** Amsterdam, Netherlands, June 1-3 (mentioned but not as primary venue)
  
**Action:** Ciprian will create and distribute a poll to gauge interest in a face-to-face meeting, including venue preferences (ICDAR in Austria vs. ICPR in France), and report results to the group. 

## Action Items

- [Ciprian: Schedule another meeting with a larger audience to continue discussions, especially on topics requiring broader board input.]
- [Ciprian: Post the hyphenation topic for further comments and call for votes from all board members on the best solution (change or no change to ALTO regarding hyphen type).] ( (https://github.com/altoxml/schema/issues/86), https://github.com/altoxml/schema/issues/43)
- [Ciprian: Ask Sebastian from BNF to provide more details and, if possible, an example ALTO file showing how BNF uses additional correction attributes, for review in the next meeting.] (https://github.com/altoxml/schema/issues/21)
- [Frederick: Investigate the current status and requirements for registering ALTO as a MIME type and report findings at the next meeting.] (https://github.com/altoxml/schema/issues/40)
- [Ciprian: Check in more detail how ALTO files are integrated with IIIF manifests and confirm current functionality.] (https://github.com/altoxml/schema/issues/31, https://github.com/altoxml/schema/issues/45)
- [Ciprian: Review the reading order and ID next functionality in ALTO, particularly regarding cross-page and cross-file references, and prepare findings for further discussion.] (https://github.com/altoxml/schema/issues/41)
- [Ciprian: Coordinate with Thomas (National Library of Netherlands) to receive a first version of the Schematron schema for ALTO, distribute to board members for testing, and collect feedback.] (https://github.com/altoxml/schema/issues/87)
- [Ciprian: Create and send out a poll to gauge interest in a face-to-face meeting (including ICPR in France as an alternative), and report results to the group.]
- [Ciprian: Write an email to the board to announce intention to step down as chair, invite expressions of interest for the chair and board member positions]

