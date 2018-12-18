# 2018-07-26 ALTO Board Meeting Minutes

**Agenda**

1. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
2. Report on registration of MIME type with IETF. [**Frederick**]
3. [Survey results](https://docs.google.com/spreadsheets/d/14LsGN42-QPAeG4gCDO2KU-QPyUTQPAELmmB7Aq5yPYg/edit?usp=sharing) for scheduling Fall face-to-face meeting. [**All**]
4. Run-through of [open Board issues](https://github.com/altoxml/board/issues). [**Art**]
5. [Survey results](https://docs.google.com/spreadsheets/d/1RcIcC3a5NYDB2AVM7C5sPuM2XJe6pdWgBIYc9bH7nuI/edit?usp=sharing) for prioritizing [open Schema issues](https://github.com/altoxml/schema/issues). [**All**]
6. Board terms and recruitment [**Frederick**]
7. Lattice structure for OCR Modeling. [**Art & Ashok**]

View all open action items [here](https://github.com/altoxml/board/labels/action%20item).

**Attending members**

* Raju Buddharaju
* Brian Geiger
* Jukka Kervinen
* Evelien Ket
* Ralph Marschall
* Clemens Neudecker
* Ashok Popat
* Art Rhyno
* Frederick Zarndt

**Minutes**

wrt agenda item 2. Frederick reported that the registration of the MIME type is still ongoing. IETF's process is challenging to 
navigate.

wrt agenda item 3. The [DLF Forum](https://www.diglib.org/dlf-events/2018forum/) in Las Vegas (October 15-17th, 2018) has a slight 
edge in the survey. Frederick and Art can commit to being there. Ashok has the best chance of joining the meeting if held on the 
Sunday of the conference (Oct. 14), Frederick will contact the organizers arranging for a meeting room in the late afternoon 
or evening of the 14th.

wrt agenda item 4. The open issues section on github is an appropriate location for ongoing activities, such as keeping the ALTO 
software page up to date. Clemens pointed out that some of the issues could be moved to schema, for example, [Find examples of text direction for  Asian languages](https://github.com/altoxml/board/issues/4). Clemens had previously had offered to consolidate and reorganize some of the github pages on the ALTO site, he will send an email to the Board with some github proposals that can be discussed at an upcoming meeting.

wrt agenda item 5 (see chart below - a higher score indicates a higer priority). Some high priority open Schema issues have lost champions. There is also a variance in the complexity of the issues, some need to be seperated out into smaller issues while others 
can be addressed with minor scema changes. One possible tool for managing the issues is to use github taging so that issues could reflect priorities. 

![Survey results for open Schema issues.](https://github.com/altoxml/board/raw/gh-pages/misc/open_schema_results.png)

A few notes on on specific issues. 

* [Draft a change proposal for "normalized" coordinates](https://github.com/altoxml/schema/issues/38) is without a draft. 
* [ALTO support for OCR of video](https://github.com/altoxml/schema/issues/46) might have some convergence with the 
[IIIF A/V group](https://iiif.io/community/groups/av/) and the
[A/V initiative in Europeana](https://pro.europeana.eu/project/audiovisual-media-task-force). Frederick is willing to champion 
this issue and there was some discussion about what it would require within ALTO, perhaps frame-based instead of page-based. Clemens 
will ask some colleages at the [Netherlands Institute for Sound and Vision](https://beeldengeluid.nl/en) on their experiences and 
will pass on the information.

It is acceptable and encouraged for the submitter of an issue to also be its champion. Art will investigate tagging the issues with 
priority levels and try to ensure that each issue has a champion.

wrt agenda item 6. Frederick reminded everyone that the Board should always be on the lookout for new members. He is currently seeking 
some with expertise with Arabic, and has contacted the Library of Alexandria. The 
[guidelines for the Board](https://htmlpreview.github.io/?https://github.com/altoxml/board/blob/master/ALTO%20Board%20Membership%20Criteria.html) 
are publically available on github. The current schedule for upcoming term expirations are as follows:

* December 31, 2018: Brian and Jean Philippe
* December 31, 2019: Clemens, Raju, and Stefan
* December 31, 2020: Art, Ashok, Evelien, Joachim, Jukka, and Ralph
* December 31, 2021: Frederick and Nate

Jean-Philippe will probably leave at the end of the year but someone from the Bibliothèque nationale de France will take his place. 
Frederick noted that renewing is usually a matter of signaling your interest to continue and that any Board member can recruit. 

wrt agenda item 7. Google has found it useful to preserve the internal uncertainty within OCR systems, and this has been done with 
a lattice structure which can include multiple hypotheses for accuracy. The lattice is a graphical structure that preserves an n-best 
list in a compact form by having nodes that correspond to the points between characters while the edges correspond to the character 
identities. Google also accommodates multiple segmentation hypotheses, and customers have benefited from the depth of information 
captured in the lattice model. 

This level of detail can also be challenging and the XML files can potentially be very large. OCR engines also do not produce this 
kind of information in a unified way. Clemens pointed out that Günter Mühlberger, an ALTO pioneer, and his group at the University of 
Innsbruck are working on handwriting and have found need for capturing variants in order to store confidence metrics. The schema for 
this work is not currently open and the confidence metrics come from [Transkribus](https://transkribus.eu/Transkribus/). Clemens 
will invite Günter and his team to participate in a call with the ALTO Board.

The Board agreed that handwritten text is within scope for ALTO and that this might be a good opportunity for ALTO to provide an  open 
standard for handwriting systems. Frederick has contacts at [Family First](https://www.familysearch.org/) and 
Brigham Young University, organizations that do research on handwriting recognition, and will check to see if there is interest in 
participating in the ALTO Board.

The next ALTO Board Meeting is tentatively set for Thursday, Sept. 20, 2018. 
