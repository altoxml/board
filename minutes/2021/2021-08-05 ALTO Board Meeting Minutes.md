# 2021-08-05 ALTO Board Meeting Minutes
1. Welcome [**All**] - special greetings to new member Thomas Haighton from the National Library of the Netherlands.
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Review recent schema issues:
   * update: 
      * [Use of LC xlink instead of w3c xlink fails in mixed validation #67](https://github.com/altoxml/schema/issues/67).
   * new:
      * [Support for encoding script direction
#73](https://github.com/altoxml/schema/issues/73).
   * pull request:
      * [Direction, orientation, and reading order (text direction elements) #74](https://github.com/altoxml/schema/pull/74).
4. Confidence value discussion redux: 
   * background materials: 
      * [Confidence value calculation #23](https://github.com/altoxml/schema/issues/23).
      * [OCR confidence in ALTO: representation, meaning, desiderata](https://docs.google.com/document/d/1JkbqfEb8pkwTdMSyjXJRfdpshlWoVbFn47uYfqB4O_Q/edit).
      * _A survey of OCR evaluation tools and metrics_ - [HIP'21](https://blog.sbb.berlin/hip2021/) paper (sent by email)
5. Upcoming Board Changes - transition of Chair position.
6. Other business. [**All**]

**Attending members**
* Ahmed Samir
* Art Rhyno
* Ashok Popat
* Brian Geiger
* Cally Law
* Ciprian Dinu
* Frederick Zarndt
* Nate Trail
* Raju Buddharaju
* Stefan Pletschacher
* Thomas Haighton

 **Minutes**

_wrt agenda item 3_. Review recent schema issues:

   * [Use of LC xlink instead of w3c xlink fails in mixed validation #67](https://github.com/altoxml/schema/issues/67) - Cip will provide some examples for the issue, at which point Art will change the label to _vote_ and indicate the proposal is for the [METS](http://www.loc.gov/standards/mets/) approach outlined in the issue.
   * [Support for encoding script direction
#73](https://github.com/altoxml/schema/issues/73) and [Direction, orientation, and reading order (text direction elements) #74](https://github.com/altoxml/schema/pull/74) - Stephan pointed out that the areas covered by these issues can be quite diverse and it might be necessary to parcel them out more. There will be a single-topic meeting on the proposal, possibly aligned with the [ICDAR conference](https://icdar2021.org/) in early September, to explore the possibilities. 

_wrt agenda item 4_. Confidence value discussion redux:

OCR confidence values and associated metrics have surfaced several times in ALTO discussions. Stefan noted that the work done for the  [HIP](https://blog.sbb.berlin/hip2021/) paper brought forward the difficulty of comparing OCR confidence numbers from different sources. It does not seem realistic to define a metric that would work across OCR engines but some constraints seem possible, for example, a consistent scale. Some reference to background material on how the calculation was arrived at would also be valuable.

Ashok pointed out that some consistency has been possible in OCR engines in areas that initially seemed difficult, for example, there was a time when unicode was not used for character sequences. Art brought forward the idea from the [meeting at DATeCH](https://github.com/altoxml/board/blob/gh-pages/minutes/2018/2018-04-24%20ALTO%20Board%20Meeting%20Minutes.md) about the use of lattices for supplying more of the raw material for calculations, and allowing confidence to be derived from a lattice structure. The potential inflation of ALTO files with lattice support could be considerable, but one approach would be to provide lattice information separately. Stefan described how [PAGE](https://github.com/PRImA-Research-Lab/PAGE-XML) had originally been conceived as a set of distinct components, and that standards like _METS_ provide packaging options.

It was agreed that the lattice discussion should continue to go forward, and that leveraging the work done for the [existing schema proposal](https://github.com/altoxml/schema/issues/57#issuecomment-510042975) would be a good basis for this direction.

_wrt agenda item 5_. Upcoming Board Changes:

Art thanked Cip for taking on the Chair position for 2022. 

_wrt agenda item 6_. Other business:

The next meeting will likely be held in connection to ICDAR in early September.
