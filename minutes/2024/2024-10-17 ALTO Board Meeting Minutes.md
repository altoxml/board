# 2024-10-17 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Topics to discuss:
    * Introduction of new board members
		* Gregor Lanzinger - Transkribus
		* Stefan Boddie - Veridian
	* In progress topics:
		* Vote for https://github.com/altoxml/schema/issues/80 - restrict PointsType to a well formed format
	* New topics to discuss:
		* Glyphs should allow CONTENT with length above 1 for cases where no precombined character exists (https://github.com/altoxml/schema/issues/85) (and related https://github.com/altoxml/schema/issues/44)
		* Make it possible to distinguish hard and soft hyphens (https://github.com/altoxml/schema/issues/86) (and related https://github.com/altoxml/schema/issues/43)
	* Reminder for updating issue (https://github.com/altoxml/schema/issues/62) (SCHEMATRON validation - checks proposals)
	* Re-open for discussion: Handwritten documents and ALTO encoding - how to make ALTO more suitable for such documents - ideas (https://github.com/altoxml/schema/issues/81)
	* New ideas for ALTO 5.0 - specially from new members, from different perspective  
3. Face-to-face meeting proposals: 
    * ICPR 2024, Kolkata, India, 1st - 5th December 2024
4. Other business. [**All**]

**Attending members**
* Cally Law
* Ciprian Dinu
* Gregor Lanzinger
* Jukka Kervinen
* Sebastien Cretin
* Thomas Haighton

**Minutes**

* Stefan Boddie could not join the meeting due to some last moment issues.
* Gregor Lanzinger from Transkribus joined the meeting as a new member, introduced himself and provided background on Transkribus and its reliance on schemas such as PageXML and ALTO formats. Gregor is working for the ReadCorp Science 2021. Currently he is CTO of Transkribus
* Reminder for voting polygonal shape format restriction issue: ([80] https://github.com/altoxml/schema/issues/80)
* Hyphen Distinction in ALTO ([86](https://github.com/altoxml/schema/issues/86)):
   - Proposal to distinguish between hard and soft hyphens in ALTO.
   - Options discussed include either a simple proposal distinguishing hard vs. soft, or a more complex solution with various hyphen variants (found for example on old Fraktur material - see also [43](https://github.com/altoxml/schema/issues/43).
   - Suggestions from the meeting, beside original proposal: Use existing subcontent attributes to differentiate hyphens and prevent redundancy. If we have a soft hyphen, this will miss from SUBS_CONTENT, in case is a hard hyphen, this appear also on SUBS_CONTENT. Further discussions planned with the proposal owner for clarity.
* Glyph Representation and Hebrew Language (not only) ([85](https://github.com/altoxml/schema/issues/85)):
   - Current constraints in ALTO is to use precomposed Unicode representation for glyphs, instead of decomposed, so one single character code should be used.
   - Proposal to allow multiple Unicode characters to represent a single glyph, especially for languages like Hebrew where precomposed forms are inadequate and in some cases is impossible to represent a glyph by a single character.
   - Discussion points included the appropriate restriction on the number of characters, currently suggested as four.
   - There is an older topic re-opened for same issue: ([44](https://github.com/altoxml/schema/issues/44))
* Advanced Validation using Schematron ([87](https://github.com/altoxml/schema/issues/87)):
   - Proposed advanced validation utilizing Schematron for more detailed checks (e.g., negative values, coordinates, encoding issues).
   - Further inputs required to finalize the testing framework and useful validation checks, till now, no significant progress was made.   
* Enhancements for handwritten text handling in ALTO:
   - Gregor discussed the challenges related to baselines and polygons in handwritten documents, emphasizing information loss when converting PageXML to ALTO.
   - On last ALTO version, base line representation is not anymore a line, but a polyline, and also for word coordinates polygonal shapes could be used
   - The different roles of ALTO and PageXML was outlined: PageXML is designed for creating and manipulating ground truth data for text recognition training, while ALTO is designed to describe the text and layout of a page, to be used on preservation and presentation systems
   - Consideration for extending ALTO's capabilities to allow more nuanced representations (e.g., handling of confidences, deep structural recursion for advanced document understanding).
   - Add relations between different ALTO nodes (a graph representation, or other types of relations)
* Efficiency Considerations:
   - Gregor brought up performance issues related to large datasets and overly complex polygons within ALTO, suggesting possible interest in more efficient, perhaps binary formats.  
* Administrative Notes:
   - Aiming for a face-to-face meeting at a major conference — potential conferences include ICFHR or ICPR. Participants requested to vote on preferences.
   - Jukka announced stepping down from the board after 15 years of service.
