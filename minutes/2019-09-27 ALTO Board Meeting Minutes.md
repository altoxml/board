# 2019-09-27 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * candidates for closing [**All**]:
      * [Change BASELINE to accommodate a list of points in addition to a single point](https://github.com/altoxml/schema/issues/32)
      * [Length of main glyph and variants](https://github.com/altoxml/schema/issues/44)
      * [TextBlocks and paragraphs](https://github.com/altoxml/schema/issues/53)
   * issue updates: 
      * [ALTO for Handwriting](https://github.com/altoxml/schema/issues/56) - [Transkribus sample](https://github.com/altoxml/board/tree/master/misc/Transkribus)
      * [Expand schema documentation for PointsType](https://github.com/altoxml/schema/issues/49) - see also PAGE-XML [add semantics to coordinate system](https://github.com/PRImA-Research-Lab/PAGE-XML/issues/13)
      * [Allow a String to contain alternative Glyph segmentation hypotheses ](https://github.com/altoxml/schema/issues/57)
   * See full list of open schema issues [here](https://github.com/altoxml/schema/issues)
4. Fall Face-to-Face Meeting:
   * confirm event - original idea for location was [2019 DLF Forum](https://forum2019.diglib.org/) but [2019-07-08 meeting](https://github.com/altoxml/board/blob/gh-pages/minutes/2019-07-08%20ALTO%20Board%20Meeting%20Minutes.md) shifted preference to [2019 IIIF Working meeting](https://iiif.io/event/2019/ann_arbor) to be held November 4-7 in Ann Arbor, Michigan. Most likely timeframe would be afternoon of Sunday, Nov. 3, _IIIF Showcase_ scheduled for Monday, Nov. 4.
   * possible topics:
      * [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) - using Ashok's [summary document](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q) to try to decide on the best approach.
      * examining lattice model proposed in [Allow a String to contain alternative Glyph segmentation hypotheses ](https://github.com/altoxml/schema/issues/57) - [XML-based syntax](https://github.com/altoxml/schema/issues/57#issuecomment-510266788) sample in issue.
      * others?
5. Upcoming Board Changes/Expirations:
   * _CCS_ : Welcome Ciprian Dinu, Managing Director (CCS Romania)
   * _December 31, 2019_: Clemens, Raju, and Stefan
   * _December 31, 2020_: Art, Ashok, Evelien, Jukka, and Ralph
   * _December 31, 2021_: Frederick, Nate, Matthew, and Ahmed Samir
6. Spring 2020 F2F Meeting Location candidates:
   * [RLUK (Research Libraries UK) 2020](https://www.rluk.ac.uk/event/rluk-conference-2020/). London, UK. March 16-18 2020
   * [Digitised newspapers - a new Eldorado for historians?](https://impresso-project.ch/news/2019/06/12/WS5-CfP.html) Lausanne, Switzerland. April 23-24, 2020
   * IFLA News Media section will sponsor a midyear meeting in Mexico City at UNAM and the National Library of Mexico (no URL or specific date yet - most likely to be held in March-May).
   * suggestions
7. Other business. [**All**]

**Attending members**
* Ahmed Samir 
* Ashok Popat
* Art Rhyno
* Cally Law
* Ciprian Dinu
* Frederick Zarndt 
* Jukka Kervinen

 **Minutes**

_wrt agenda item 1_. The Board welcomed Ciprian (Cip) Dinu from CCS. Cip described his extensive background in ALTO, going back to the EU-funded  METAe project in 2000 and his work on the first software to ever produce ALTO files. 

_wrt agenda item 3_. Review recent schema issues:

   * [Change BASELINE to accommodate a list of points in addition to a single point](https://github.com/altoxml/schema/issues/32) - the syntax generally agreed to at the [March 18, 2018 meeting](/altoxml/board/blob/gh-pages/minutes/2018/2018-03-12%20ALTO%20Board%20Meeting%20Minutes.md) will be updated to change _single line_ to _polyline_. Art will update the issue and seek a vote on github so that this change can be part of the next ALTO revision.

   * [Length of main glyph and variants](https://github.com/altoxml/schema/issues/44) and  [TextBlocks and paragraphs](https://github.com/altoxml/schema/issues/53) will be closed with a note acknowledging their informational nature and that they don’t have a schema implication.

   * Ashok noted that recent work has been done on [ALTO - PAGE xml: Object mapping and possible transformation generation](https://github.com/altoxml/schema/issues/48) by [Christian Clausner](https://github.com/chris1010010). In response to a question from Frederick, Ashok highlighted a couple of developments at the recent [ICDAR conference](https://icdar2019.org/) that might have a connection to ALTO:
      * Increasing emphasis on making datasets available for public use. This is useful for competitions and testing, page segmentation analysis, text-finding, and other emerging research areas.  [Note that this has synergy with the recent announcements for public ground-truth datasets made at [DH2019](https://www.newseye.eu/blog/news/a-perspective-on-research-on-digitised-newspapers-at-dh20190/)].
      * These datasets can have minimal formatting at this point due to their ad-hoc nature, but this is a promising trend for standards like ALTO and PAGE, and for advancing text analysis technologies in general.          

   * The [XML syntax used by Transkribus for handwriting ](https://github.com/altoxml/board/tree/master/misc/Transkribus) was highlighted as a production example for the [ALTO for Handwriting](https://github.com/altoxml/schema/issues/56) issue.

   *  The github issues for [Expand schema documentation for PointsType](https://github.com/altoxml/schema/issues/49)  and [Allow a String to contain alternative Glyph segmentation hypotheses ](https://github.com/altoxml/schema/issues/57) have seen substantial activity since the last Board meeting. The _lattice_ discussion has largely become embedded in the _Glyph_ issue. Ashok noted that the related thread on the _optical model score_ and  _language score_ in the issue could use further clarification from his group and he could bring forward some concrete examples at an in-person meeting.

_wrt agenda item 4_. Fall Face-to-Face Meeting:

There was general agreement that encoding OCR uncertainty and alternative hypotheses via a _lattice_, or similar model, would be a good topic for the Fall F2F gathering. The meeting will be held right before the [2019 IIIF Working meeting](https://iiif.io/event/2019/ann_arbor). The IIIF event runs November 4-7 at the University of Michigan campus in Ann Arbor, Michigan, and the F2F meeting will be held Sunday, Nov. 3 from 3 to 6 pm at the [aadlfreespace room](https://aadl.org/rooms) of the downtown branch of the [Ann Arbor District Public Library](https://aadl.org/). This location is about a [10 minute walk from the U. of Michigan campus](https://www.google.com/maps/dir/University+of+Michigan,+South+State+Street,+Ann+Arbor,+MI/Ann+Arbor+District+Downtown+Library,+343+S+5th+Ave,+Ann+Arbor,+MI+48104/@42.2791219,-83.7444076,17z/data=!3m1!4b1!4m14!4m13!1m5!1m1!1s0x883cae38e7de1701:0x5ba14e5178e997e3!2m2!1d-83.7382241!2d42.2780436!1m5!1m1!1s0x883cae3eaf9d3609:0x4d7bd3ac7d918e68!2m2!1d-83.7460357!2d42.278043!3e2?hl=en). Art will ensure that Stefan and Christian are made aware of the meeting, and will extend an invitation to the [Text Granularity Technical Specification Group](https://iiif.io/community/groups/text-granularity/), as well as to [Robert Sachunsky](https://github.com/bertsky), who has proposed an XML syntax for lattices for ALTO based on [work done for PAGE](https://github.com/OCR-D/spec/issues/72#issuecomment-469019453).

_wrt agenda item 5_. Upcoming Board Changes/Expirations:

Art will check with Clemens, Raju, and Stefan about their plans in light of the upcoming expiration dates for their terms on the Board. Ashok may be passing on his membership to one of his team as he takes on broader duties at Google. Art will be assuming a Chair position on another Board in January 2021 and will be looking to pass the torch at the end of next year.

_wrt agenda item 6_. Spring 2020 F2F Meeting Location candidates:

The [Digitised newspapers - a new Eldorado for historians?](https://impresso-project.ch/news/2019/06/12/WS5-CfP.html) conference was seen as a good opportunity to present a paper on ALTO, and it would make sense to then use the event as an opportunity for a Spring F2F meeting.

_wrt agenda item 7_. Other business.

The next meeting will be scheduled after the Fall F2F meeting.
