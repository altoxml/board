# 2025-05-28 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Topics to discuss:
    * Introduction of new board members
		* Gregor Lanzinger - Transkribus
		* Stefan Boddie - Veridian
	* In progress topics:
		* Vote for https://github.com/altoxml/schema/issues/80 - restrict PointsType to a well formed format 
		* Glyphs should allow CONTENT with length above 1 for cases where no precombined character exists (https://github.com/altoxml/schema/issues/85) (and related https://github.com/altoxml/schema/issues/44)
		* Make it possible to distinguish hard and soft hyphens (https://github.com/altoxml/schema/issues/86) (and related https://github.com/altoxml/schema/issues/43)
	  * Validation of ALTO via SCHEMATRON (https://github.com/altoxml/schema/issues/62) (SCHEMATRON validation - checks proposals)
   * New topic:
     * Relation between different ALTO components (https://github.com/altoxml/schema/issues/88)  
	* New ideas for ALTO 5.0 - specially from new members, from different perspective  
3. Face-to-face meeting proposals: 
    * ICDAR 2025, Wuhan, China, 16th - 21st September 2025
4. Other business. [**All**]

**Attending members**
* Ashok Popat
* Stefan Boddie
* Gregor Lanzinger
* Raju Buddharaju
* John Loitzenbauer
* Ciprian Dinu

**Minutes**

1. New Board Member Introductions

* Stefan Bodie (DL Consulting / Veridian)
	* Founder of DL Consulting, creators of the Veridian digital library platform, widely used for digitized newspaper collections.
	* Has worked with METS/ALTO formats for ~20 years, starting with the National Library of New Zealand project (~2006).
	* Veridian primarily consumes ALTO rather than producing it.
	* Usage is basic/stable, not leveraging many newer ALTO features.
	* Has collaborated with CCS since early METS/ALTO adoption.
	* Joining the board to contribute from a platform implementer perspective.

* Gregor Lanzinger (READ-COOP / Transkribus)
	* CTO at READ-COOP, developers of Transkribus.
	* Focus on Handwritten Text Recognition (HTR), but also printed text.
	* Their main schema is PAGE XML, with ALTO as a frequently used secondary format.
	* Interested in direction of ALTO development and in providing feedback from HTR workflows.

2. ALTO 5.0 Roadmap Direction

* The group is working toward ALTO 5.0, with goals:
	* Remove inconsistencies
	* Clean deprecated or unused elements
	* Fix backward compatibility concerns
	* Introduce new features where needed (input from implementers requested).

3. Technical Topic Discussions

* Topic [#80](https://github.com/altoxml/schema/issues/80) – Restricting the POINTS data type
	* Proposed change to define a strict format using a regular expression, improving consistency in coordinate values.
	* The change exists as a GitHub branch and the group was asked to vote by commenting “accept”.
	* Some hesitation due to the complexity of the regex, and few votes received so far.
	
	* Actions: 
		* Members should review and vote on GitHub.

* Topic [#85](https://github.com/altoxml/schema/issues/85)/[#44](https://github.com/altoxml/schema/issues/44): Glyph Representation Length
	* Current ALTO specification forces glyphs to be represented by exactly one Unicode code point.
	
	* This is problematic because:
		* Some scripts cannot be represented using a single precomposed Unicode character.
		* Languages affected include Hebrew, Thai, multiple South Asian scripts, and others using combining diacritics.
		* Some characters require a decomposed sequence of multiple Unicode code points.

	* Discussion Points:
		* Previous proposal suggested raising the limit to maximum length = 4 code points, based on known cases in Hebrew and Thai.
		* However, participants noted:
			* Some writing systems may require more than 4 mark combinations.
			* It is difficult to define a universal upper bound.
			* Limiting length in the ALTO standard offers no real benefit.

	* Conclusion:
		* The group agreed the best solution is to remove the glyph length restriction entirely.
		* A change request will be prepared:
			* Glyphs may contain Unicode strings of arbitrary length.
			* This change will be submitted as a new branch and put up for voting.

	* Actions:
		* Update glyph-length specification to remove fixed limit	- Ciprian
		* Notify topic owner and prepare new change request - Ciprian
		* Members should review and vote on GitHub - all members	
	
* Topic [#86](https://github.com/altoxml/schema/issues/86)/[43#](https://github.com/altoxml/schema/issues/43): Hyphen Handling in ALTO
	* The group revisited a previous proposal to clarify how hyphens at line breaks should be treated in ALTO output.
   
	* The issue arises because hyphens in text can represent different things:
		* Soft hyphen (used only for line-breaking; should be removed when text is reflowed)
		* Hard hyphen (a real part of the word; should be preserved)
		* Other special hyphen-like characters (e.g., longer dashes or script-specific hyphens)
    
	* Original Proposal:
		* Add a new attribute to the <HYP> element to indicate whether the hyphen is soft or hard.
    
	* Alternative Consideration:
		* Use a more general attribute like hyphenType to represent multiple hyphen categories.
    
	* Final Preferred Solution (Consensus Reached):
		* Do not change the schema.
		* Use the existing content attribute of <HYP> to store the actual Unicode character for the hyphen.
		* Downstream processors can decide how to treat the hyphen (remove it, preserve it, or interpret it in context).
    
	* Rationale:
		* Unicode already distinguishes various hyphen types.
		* OCR engines should primarily transcribe what is on the page, not infer meaning.
		* This avoids adding complexity to the ALTO standard and preserves maximum information.
		* Interpretation (soft vs. hard hyphen handling) should be done at post-processing stage, not encoded in ALTO.
    
	* OCR Perspective:
		* OCR engines may not reliably differentiate soft vs. hard hyphens visually.
		* However, if the engine can detect the specific Unicode character, this information should be stored and not overwritten.
		* Transcription should be lossless, interpretation should happen later
    
	* Actions:
		* Open the change for board voting - Ciprian
		* Board members review and comment / vote for closing the topic	- All members

* Topic [#62](https://github.com/altoxml/schema/issues/62): Value Restrictions & Validation in ALTO
  * The group discussed how to handle numeric value constraints in ALTO (e.g., coordinates, confidence, accuracy).
    
  * Key Points:
    * Lower-bound constraints (e.g., requiring values to be positive) are easy to apply in the current XSD schema.
    * Upper-bound constraints (e.g., ensuring coordinates stay inside the page) are not realistically enforceable with XSD 1.0.
    * XSD 1.1 would allow these checks, but few processors support it, making adoption impractical.
    
  * Decision:
    * Introduce an optional Schematron schema (add-on) for more complex logical validations (e.g., word is inside line, line inside block, etc.).
    * This Schematron supplements, not replaces, the core XSD schema.
    * Schematron will focus first on coordinate hierarchy consistency.
    
  * Accuracy attribute range subtopic:
    * The accuracy attribute lacks constraints in the current schema, though documentation suggests it should be 0–100.
    * Other metrics like WC (word confidence) and PC (page confidence) already enforce 0–1.
    
  * Discussion Points:
    * Some argued accuracy might represent different metrics, not always OCR quality, and may not always range 0–100.
    * However, documentation currently assumes 0–100, so aligning the schema with the documentation is clearer and consistent.

  * Outcome:
    * Proposal: Add a 0–100 constraint for accuracy.
    
  * Schematron Development Update:
    * Thomas is drafting the first Schematron rules.
    * Will include:
			* Page > Block > Line > Word containment checks
    * Initial implementation will be shared for testing and feedback.
    
  * Actions:
    * Prepare a separate branch with this accuracy restriction for voting - Ciprian
    * Board members review and comment/vote - all members
    * Thomas will continue with Schematron

* Topic [#88](https://github.com/altoxml/schema/issues/88) (new): Relations Between ALTO Components
	* Discussion about whether ALTO should support explicit semantic or structural relationships between elements (e.g., footnote marker → footnote text, table cell → column header, image → caption).
	* This would allow non-hierarchical links, similar to METS SMLinks.

	* Concerns & Perspectives:
		* ALTO is fundamentally about layout + text, not semantic interpretation.
		* Some of these relationships currently belong in METS, especially across pages.
		* Value depends on whether ALTO should express document understanding vs. pure OCR output.
    
	* Status:
		* Exploratory / No decision yet.
		* Group will collect more use cases before deciding if this direction is worth pursuing.
    
	* Actions:
		* Collect use cases for cross-object relationships - all members

4. Future ALTO 5.0 Direction:
   
	* So far, ALTO 5.0 is mostly cleanup and simplification (removing outdated attributes, removing XLink, etc.).
	* No major new features yet — open for ideas.
	* Long-Term Need Identified: Text Correction / Versioning Support
	* Libraries often crowdsource OCR corrections.
	* Currently, corrections are stored outside ALTO → difficult to reintegrate.
	* Interest in supporting:
		* Text alternatives at line or block level
		* Possibly some form of versioning or corrected-text overlay
	* This is recognized as a difficult but important long-term feature, to revisit in future discussions.

6. Board Membership:
  * Several board members are stepping down (Brian, Yukka, Raju at the end of 2025).
  * Ciprian would like to step down from Chair position by the end of 2025, latest middle of 2026, any candidate proposal this position is welcomed
  * Group is encouraged to propose new members, ideally maintaining representation from key institutions

  * Actions:
    * Identify candidates for new board members - all members
    * Identify a candidate for Board Chair position - all members
