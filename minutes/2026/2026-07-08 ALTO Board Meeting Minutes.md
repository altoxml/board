# 2026-07-08 ALTO Board Meeting Minutes

1. Welcome [**All**]
2. Organisatoric topics:
  * Look for next Chair of ALTO Board (starting from January 2027)
    * Express your interest and/or propose candidates
  * Face-to-face meeting on ICDAR 2026, Viena, Austria 30th August - 4th September 2026
    * Decide best day/day time for the meeting
    * Estimate number of participants (from Board, but also from other comunities, interested on topic)
    * Decide if we will have a hybrid meeting, or only on-site meeting
    * Main topic(s) to discuss on face-to-face meeting
3. In progress topics:
  * Votes for topics on "voting" status - review and vote for all
  * SCHEMATRON validation (https://github.com/altoxml/schema/issues/87) 
  * Add "MultiPolygon" as option for "ShapeType" - new proposal, possible for 5.0 (https://github.com/altoxml/schema/issues/90)
	
**Attending members**
* Thomas Haighton
* Sebastien Cretin
* Ashok Popat
* John Loitzenbauer
* Hany Abdellatif
* Ciprian Dinu

## Key Takeaways

- Ciprian announced his intention to step down as ALTO Board chair after five years and is seeking a successor.
- The face-to-face board meeting at ICDAR (Vienna) is being planned as a hybrid meeting, tentatively scheduled for an afternoon session during the main conference.
- A first version of SCHEMATRON validation for ALTO files has been prepared on a new GitHub branch; board members are encouraged to test it.
- A proposal was raised to support multi-polygon shapes in ALTO to represent complex shapes such as donuts (e.g., stamps with circular text).
- The topic of encoding the "long S" character in historical Latin documents was discussed, with guidance provided on best practices.

---
## Discussed Topics

### 1. Chair Position Transition

Ciprian opened the meeting by announcing his intention to step down from the ALTO Board chair position after five years, citing the value of fresh perspectives and new ideas. He noted that no responses had yet been received following his prior email on the subject. He clarified that the role is primarily organizational rather than technical, and suggested that a candidate from outside the current board could also be considered, though a board member would be preferable.
- **Details**
    - Ciprian: Has held the chair position for five years and believes it is time for a change; no candidates have come forward yet.
    - Ciprian: Mentioned a possible option of appointing someone from CCS, in which case he would step down from the board to avoid over-representation from one entity.
    - Thomas: Asked whether any board members had expressed interest; none had at that point.
- **Conclusion**
    - Ciprian will follow up via email to solicit nominations or expressions of interest from all board members.

---
### 2. Face-to-Face Meeting at ICDAR (Vienna)

The group discussed logistics for the upcoming in-person board meeting to be held during the ICDAR conference in Vienna. Topics covered included the best day and time, meeting format (hybrid vs. on-site only), expected attendance, and the agenda focus.
- **Details**
    - Ciprian: Proposed holding the meeting during main conference, not during workshops/tutorial days, in the afternoon (around 15:30 Vienna time), coinciding with the period when ICDAR organizer board discussions typically take place, to maximize availability.
    - Ciprian: Proposed a hybrid format to accommodate remote participants and cover multiple time zones; noted that Clemens had already confirmed a room should be available, though the specific room type is pending headcount.
    - Ciprian: Suggested the meeting agenda focus on collecting ideas and feedback from attendees — including guests from other communities — rather than a single deep-dive technical topic, given the expected mixed audience.
    - Sebastien: Confirmed availability and agreement with the proposed time and hybrid format;
    - Ashok: Confirmed he will be the only Google representative attending ICDAR; agreed to keep an eye out for other interested contacts.
- **Conclusion**
    - Hybrid meeting format is preferred, targeting an afternoon slot (~15:30 Vienna time) during the main ICDAR conference days.
    - The agenda will focus on open idea collection and community feedback rather than a single technical topic.
    - Ciprian will send a follow-up email to gather headcount and finalize room requirements with Clemens.

---
### 3. Voting on ALTO Version Topics

Ciprian reminded board members to cast their votes on the proposed topics for the next ALTO version (primarily version 5.0). He noted that several topics currently lack sufficient votes
- **Details**
    - Ciprian: Highlighted that many topics in voting status still lack votes and urged all members to participate.
- **Conclusion**
    - Board members are asked to review and vote on all open topics in GitHub.

---
### 4. Schematron Validation — First Version Presentation (issue https://github.com/altoxml/schema/issues/87)

Ciprian presented the first version of Schematron validation for ALTO files, prepared in a new GitHub branch with significant contributions from Thomas. The presentation included a walkthrough of the test categories, validation methods, and a live demonstration using a modified ALTO file.
- **Details**
    - Ciprian: Described test categories including coordinate validation (negative values, out-of-page coordinates, containment of text lines within text blocks and strings within text lines), empty container checks, font size and confidence value checks, reference integrity checks, overlapping object detection, and hyphenation validation.
    - Ciprian: Presented two validation methods — an open-source pipeline and Oxygen XML editor — with the open-source method generating a large XML report that can be transformed into a readable HTML summary.
    - Ciprian: Showed a live example where a manually corrupted ALTO file triggered errors (negative width, invalid vertical position) and warnings (text block coordinates outside print space, overlapping blocks).
    - Ciprian: Explained that some issues are flagged as errors, others as warnings, and others as informational, with severity levels still subject to refinement based on community feedback.
    - Ciprian: Mentioned that Clemens intends to run the Schematron on a large collection of ALTO files for broader testing.
    - Ciprian: Raised the possibility of language-specific tests (e.g., Chinese characters should not be grouped into multi-character strings).
    - Thomas: Confirmed coverage of the topic; prepared the validation instructions and open-source pipeline.
    - Sebastien: Expressed preference for the open-source validation option and confirmed he will test it.
    - Ashok: Expressed interest in testing the Schematron against Google's ALTO file collection and potentially contributing additional test ideas.
- **Conclusion**
    - The first Schematron version is available on a new GitHub branch for community testing (https://github.com/altoxml/schema/tree/issue87/v5).
    - Board members are encouraged to test it on their respective collections and provide feedback.
    - Future enhancements may include polygon-based containment and overlap tests.

---
### 5. Multi-Polygon Shape Proposal (issue https://github.com/altoxml/schema/issues/90)

Ciprian introduced a question raised by a colleague regarding the representation of complex shapes (e.g., donut shapes) in ALTO, such as a stamp with circular text surrounding an inner illustration.
- **Details**
    - Ciprian: Explained that ALTO currently supports polygon, ellipse, and circle shapes, but only simple (non-compound) polygons. A multi-polygon element — a collection of two or more polygons — was proposed as a solution.
    - Ciprian: Noted an alternative of modifying the polygon syntax to allow multiple sub-shapes, but considered the multi-polygon approach cleaner.
    - Sebastien: Suggested disk labels with circular writing as another practical use case.
- **Conclusion**
    - The proposal will be opened for broader community discussion before being put to a vote.
    - The extension is considered relatively simple and unlikely to cause compatibility issues.

---
### 6. Encoding the "Long S" Character in Historical Documents

Hany raised a question about how to handle the historical "long S" character (resembling an "f") found in old Latin and French documents when generating ALTO files.
- **Details**
    - Hany: Described encountering the "long S" in very old Latin and French documents and questioned whether to encode it as its Unicode character or normalize it to a standard "s" for searchability.
    - Ciprian: Recommended encoding the "long S" as-is in the ALTO file to faithfully represent the original document; normalization to standard "s" should be treated as post-processing only.
    - Ciprian: Described CCS's approach: replacing "long S" with "standard S" only when the resulting word is validated against a dictionary, minimizing errors (as post processing).
    - Hany: Confirmed having implemented a similar additional layer to distinguish genuine "f" characters from "long S" using dictionary checks.
- **Conclusion**
    - Best practice is to preserve the original "long S" encoding in the ALTO file; normalization to standard "s" should be handled as a separate post-processing step, not embedded in the ALTO output.

---
### 7. New Board Member Contacts

Ciprian reminded John that he had previously mentioned colleagues who might be interested in joining the ALTO Board but had not yet shared their contact details.
- **Details**
    - Ciprian: Asked John to send the contact information for potential board member candidates.
    - John: Confirmed he would send the contacts as soon as possible.
- **Conclusion**
    - John will provide contact details for prospective board members.

---
## Action Items

- **Ciprian**
    - Send a follow-up email to all board members summarizing the chair succession discussion and soliciting nominations or expressions of interest.
    - Send a follow-up email summarizing ICDAR face-to-face meeting proposals (date, time, hybrid format, agenda focus) and collect headcount from all members.
    - Coordinate with Clemens on room requirements for the ICDAR face-to-face meeting once headcount is confirmed.
    - Open the multi-polygon shape proposal for broader community discussion and, pending feedback, put it to a vote.
    - Prepare meeting summary covering all topics discussed today.
- **John**
    - Send Ciprian the contact details for the potential new board member candidates.
- **Sebastien**
    - Test the Schematron validation tool (open-source option) on BNF ALTO files and provide feedback.
- **Hany**
    - Test the Schematron validation tool on available ALTO files, particularly Arabic-language documents, and report any findings or suggestions.
- **Ashok**
    - Test the Schematron validation tool on Google's ALTO file collection and share feedback or additional test ideas.
    - Keep an eye out for contacts outside Google who may be interested in attending the ICDAR face-to-face board meeting and inform Ciprian.
- **All board members**
    - Review and cast votes on all open ALTO version topics in the GitHub voting system.
    - Notify Ciprian of anyone interested in the chair position or in attending the ICDAR face-to-face meeting.
	- Test the Schematron validation tool and provide feedback.
