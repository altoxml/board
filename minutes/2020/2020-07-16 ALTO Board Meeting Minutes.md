# 2019-07-16 ALTO Board Meeting Minutes
**Agenda**
1. Welcome. [**All**]
2. Discussion of handwriting support in ALTO. [**All**]
   * some ALTO examples from current projects ([source image](https://github.com/altoxml/board/raw/gh-pages/misc/Vol-1-Intro-0001.jpg)):
      * [xml](https://github.com/altoxml/board/raw/gh-pages/misc/Vol-1-Intro-0001_scripta.xml) - [eScriptorium](https://gitlab.inria.fr/scripta/escriptorium)
      * [xml](https://github.com/altoxml/board/raw/gh-pages/misc/Vol-1-Intro-0001_transkribus.xml) - [Transkribus](https://transkribus.eu/Transkribus/)
   * related issues?
      * [Reading Order (IMPACT) #18](https://github.com/altoxml/schema/issues/18)
      * [ALTO support for encoding OCR segmentation ambiguity #63](https://github.com/altoxml/schema/issues/63)
3. Other business. [**All**]

**Attending members**

* Ahmed Samir
* Ashok Popat
* Art Rhyno
* Cally Law
* Art Rhyno
* Ciprian Dinu
* Frederick Zarndt
* Hany Abdel Hamid Elsawy
* Jukka Kervinen
* Raju Buddharaju

**Guests**

* Benjamin Kiessling

**Minutes**

The Board welcomed Ben to the meeting. After some introductions, Ben
provided a snapshot of his experiences with ALTO from his work with
[kraken](https://github.com/mittagessen/kraken) and handwriting
recognition. He flagged the importance of encoding reading order, a
function that needs a level of granularity and is not supported by any
current serialization format. Art brought up ALTO's existing [reading
order ticket](https://github.com/altoxml/schema/issues/18), which has
become dated but has also been flagged relatively recently as a high
priority.  Ben noted that the ticket seemed to be based on regions, which
is very tailored to print resources, and that block approaches do not work
nearly as well on manuscripts, which can have many disconnected parts.

Cip pointed out that ALTO arguably has order on the block level through
IDNEXT, and Ben recalled a conversation with Clemens from a few years ago
where there was a sense that an explicit reading order might more properly
belong in METS. Jukka asked if the existing ALTO issue could be augmented
to have ordered and unordered groups. Ben will consult with some colleagues
and investigate opening a new github issue, or adding to the existing issue.

In addition to reading order, the other discussion that has been linked to
handwriting support has been encoding segmentation ambiguity. Ben has only
encountered the need for a data format for uncertainty in very specialized
circumstances, and noted that the additional overhead in parsing and memory
would make it unlikely for it to be included in normal workflows. Ben noted that
ALTO is currently the exchange format for the
[eScripta](https://escripta.hypotheses.org/) project from 
Université Paris Sciences et Lettres (PSL). He
contributes to this PSL initiative, which 
uses _kraken_ for recognition support with manuscripts.

Ashok described two handwriting projects at Google, one based on
strokes entered on mobile devices, and another purely optical approach,
where handwriting is treated like a font. He noted that more recent text
processing produces confidence values that are aggregated at various
levels, and that partners have received these values at the level
requested, from calculations for individual graphenes/characters through to
words, lines, and paragraphs. One useful technique has been to apply an
array of different language models to determine if the text resembles any
known language.

Reading order has been captured in Google's processing using a format
called ROUTS, where multiple paths through a page can be described. This
has not been typically needed in current book scanning but it might have had 
more application in the 
[Google newspaper project](https://news.google.com/newspapers), which was 
halted in 2011. There  has been recent interest in technologies from the 
newspaper project, and Ashok will follow-up on how paths are managed in 
case it might contribute to a possible ALTO encoding.

Frederick noted the common role of METS for ordering article-level regions
in the many newspaper projects that he has worked on. Ben pointed out that
manuscripts often have very fine-grained insertions and could create
problematic situations in METS, for example, necessitating ALTO files
encoding a single character. The _eScripta_ project surfaces these
requirements by targeting a complete platform for textual analysis for
almost any material that a humanist would have interest in. Not only for
recognition but also for supporting research areas like paleography. Ben
highlighted the open nature of _eScripta_, all code is  open source, and
models created in the project can be freely shared with others.

Jukka asked if ALTO support for handwriting might argue for creating new
elements for capturing characteristics of content like the style of  written 
text, similar to FONT for printed text, and would there be interest in recording 
details like the type of pen or pencil used. Ben questioned whether it would be
better to punt to TEI for these areas, a complimentary XML standard that
many humanists would already be familiar with. Jukka pointed out that ALTO has
provision for referencing external XML, so there would be options for
leveraging TEI documents from within ALTO files.

In response to some questions about the ALTO samples exported from
_eScripta_, Ben noted that _kraken_ has more granular ALTO support, and encodes
individual words and the underlying glyphs. Ben pointed out that ALTO could
use more attention in areas like the current documentation of polygons, and
that he, like others, has been confused by the role of the space (SP) tag.
Art flagged the SP [github issue](https://github.com/altoxml/schema/issues/54) 
and the resulting extended discussion of the SP element at the
[2018-11-29 Board meeting](https://github.com/altoxml/board/blob/gh-pages/minutes/2018/2018-11-29%20ALTO%20Board%20Meeting%20Minutes.md), 
where these seemed to be some consensus that SP could benefit from a CONTENT attribute.

The meeting ended with a discussion about the future of OCR and HTR
engines. _Kraken_ specifically targets marginalized languages and non-latin
scripts that do not get much attention from commercial engines. Ben
reiterated the preference for open solutions and Ashok highlighted the
possibilities of collaborations between open source projects and industrial
research initiatives. The Board thanked Ben for his invaluable insights
into handwriting technologies.
