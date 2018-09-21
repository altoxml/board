# 2018-09-20 ALTO Board Meeting Minutes

**Agenda**

1. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
2. Update on support for ruby characters. See [issue 51](https://github.com/altoxml/schema/issues/51). [**Art/Frederick**]
3. GitHub Reorganization and Housekeeping. [**Clemens & Others**]
   * Status/migration of wiki – see https://altoxml.github.io/
   * Process for schema changes
4. Planning for F2F meeting (Oct. 14, [DLF Forum](https://www.diglib.org/dlf-events/2018forum/) in Las Vegas). [**All**]
5. Champions for orphaned/unassigned [open schema issues](https://github.com/altoxml/schema/issues). [**Art**]
6. Results of vote for two new Board Members/expansion of Board. [**All**]

View all open action items [here](https://github.com/altoxml/board/labels/action%20item).

**Attending members**

* Art Rhyno
* Ashok Popat 
* Brian Geiger
* Clemens Neudecker
* Frederick Zarndt
* Joachim Bauer
* Jukka Kervinen
* Raju Buddharaju
* Ralph Marschall
* Stefan Pletschacher 

**Minutes**

_wrt agenda item 2_. Frederick gave some background on [issue 51](https://github.com/altoxml/schema/issues/51). He is working on 
two projects that involve the digitization of Japanese-American newspapers, one with the University of California, Riverside, and 
the other with Stanford University, the Hoover Institution, and East View Information Services. Ruby characters have been 
problematic for OCR processing in these projects. Raju has experience with text materials with ruby characters from years ago, 
noting that they are usually associated with words in Japanese and are most often a clue for pronunciation. Frederick noted the 
synergy with Hebrew and Arabic where dots and dashes are used in a similar manner. 

Ashok suggested that ALTO support could function on two levels, one for representing text so that it can be rendered properly, 
and also at a higher functional level for tasks like producing audio books and supporting text mining. Stefan flagged the potential 
for complex XML when encoding interpretations or analysis of glyphs, using the example of ligatures and the verbosity associated 
with specifying different glyph combinations and variants. It was  noted that Japan has a long history with digitization projects, 
and that it might be useful to invite someone from Japan with OCR experience for ruby characters to the Board. Frederick has 
approached someone at the [National Diet Library](http://www.ndl.go.jp/en/) in the past. Clemens has a colleague who has transcribed 
a large amount of Japanese materials at the Diet and currently lives in Japan, who he will contact.

_wrt item 3_. Art asked about the relationship between _github_ and _github.io_ ALTO sites. Clemens pointed out that 
[altoxml.github.io](https://altoxml.github.io/) is used to provide a more accessible/friendly space into ALTO. Github is used for 
working through ALTO materials and _github.io_ is more for the public-facing, final renditions of ALTO materials. Art will ask about 
changing the link on the Library of Congress site to go to _altoxml.github.io_. The process for schema changes was also clarified. The 
champion for an issue can notify the Board by email between meetings to comment ACCEPT or REJECT on the issue, and the 
proposal can  then be formally accepted or rejected at the next meeting.

_wrt item 4_. One of the newest Board members, Ahmed Samir from Bibliotheca Alexandrina, will be at the DLF conference and it would be 
an opportune time to work through supporting Arabic in ALTO. Clemens noted that it would be worthwhile to ask Ahmed to bring materials 
from  Bibliotheca Alexandrina to the meeting and Stefan suggested that new Board members be informed that materials they contribute 
will be made available by public by a _CC BY-SA 4.0_ license. Frederick will update the 
[ALTO Board Membership Criteria](https://github.com/altoxml/board/blob/gh-pages/ALTO%20Board%20Membership%20Criteria.html) to reflect 
the licensing expectation.

_wrt item 5_. There are only a few schema issues without champions. It is unclear if Jean-Philippe’s replacement from 
Bibliothèque nationale de France will champion the same tickets but Frederick will follow up on Jean-Philippe’s plans. There was 
some discussion about [Issue #38](https://github.com/altoxml/schema/issues/38) regarding “normalized” coordinates, where absolute 
pixel values are replaced with fractional values based on a coordinate system with (0,0) at the origin and (1,1) on the opposite 
corner. This would allow the same set of coordinates to be used on the same image as it is resized. Clemens noted that the Bavarian 
State Library took a similar approach to TEI more than a decade ago, and Frederick had also seen a related model at iArchives. 
Clemens will add himself to the issue and work with Frederick on a proposal. Art will close [Issue #50](https://github.com/altoxml/schema/issues/50).

_wrt item 6_. The Board will expand to allow for both Ahmed Samir and Matthew Thomas Miller to join at the same time.

_Other business_. Jo has identified a problem with _processingStepType_ in version 4. He discussed the situation with Jukka and has a 
proposal that will not break backwards compatibility. The _Processing_ elements will also be applicable at more than the page level of texts. Jo will create an issue for this.

The next ALTO Board Meeting is tentatively set for Thursday, Nov. 29, 2018 at 9am EST. 
