# 2022-04-14 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Thank you Art and welcome John Loitzenbauer [**All**]
4. General topic: improve the voting process [**All**]
5. Issues to discuss:
    * Language encoding related:
      * Support for script in addition to language (https://github.com/altoxml/schema/issues/70)
      * Add LANG and ROTATION attributes to Page element (https://github.com/altoxml/schema/issues/55)
      * Storing detected languages (https://github.com/altoxml/schema/issues/66)
    * Coordinates related:
      * Restrict float attribute values where possible to allow for better xml-validation (https://github.com/altoxml/schema/issues/62) 
      * Expand schema documentation for PointsType (https://github.com/altoxml/schema/issues/49)
6. Face-to-face meeting proposal: check survey result [**All**]
7. Other business. [**All**]

**Attending members**
* Sebastien Cretin 
* Ciprian Dinu 
* Thomas Haighton
* Jukka Kervinen
* Cally Law
* John Loitzenbauer
* Art Rhyno
* Frederick Zarndt

 **Minutes**

We have started the meeting with few nice words from Art and John as new member of ALTO Board - John is technical lead for digitization department of CRKN and responsible for technical infrastructure, scanning and OCR.

Next discussed topic was related to a general topic: voting process. Based on previous discussion several topics were prepared for voting so that we can include them on 4.3 version, but voting process was quite slow, till the current meeting only 4 votes were given for each topic (and we need 12 for a 2/3 majority). Several ideas were proposed: setting a deadline not only a version as a milestone, send reminder e-mails, for entire group or individual, pointing out the topics to be voted. 

Regarding opened issues, five topics were discussed, grouped into two categories - language related and coordinates system related:

Language related:

https://github.com/altoxml/schema/issues/70 - in this topic there are several proposals for adapting ALTO schema to allow additional attributes beside LANG to encode the used script. There are also proposals to adopt maybe a different standard like BCP 47 instead what we use now to define the used language on different sections of the document. Reviewing definition of xsd:language (the type of LANG attribute) we figure out this covers as well the script encoding (according with RFC 1766 ( https://www.rfc-editor.org/rfc/pdfrfc/rfc1766.txt.pdf ) ). Frederick mentioned that "script" could be related mainly to handwritten text, or other types of writing (like Arabic language) where letters are joint to form words. He raise a question if we can encode this as well (English Handwriting for example), as "script" word meaning leads to handwritten text. Probably this can be better encoded on text formats section, since is more about the font, rather than "script" in the meaning of this current topic. A possible extension could be to define language using two attributes like value itself and standard used (f.e. in METS, a date is represented in this way - encoding used and value itself). This option will also break back-compatibility, but could be a way to use in the future any standard we want to express languages/scripts. The final proposal was to close the topic and not to make any changes and also details about how we can express script beside language were added into topic comments. Also changing to another standard will break back-compatibility. The topic was set for voting (if agree to close it, please vote with ACCEPT).

https://github.com/altoxml/schema/issues/55 - this topic is about adding LANG and ROTATION attribute as default value also on highest level of the document, this means Page level. In ALTO a series of attributes have default values defined at any level, and inheritance is used for lower levels, with option to overwrite value. For LANG/ROTATION highest level is not the Page but Block. Also on topic discussions was mentioned that maybe one language is not enough and we should use a list of languages, but this would give a different meaning to LANG attribute - instead of default language, to available/present languages. The proposal was to add LANG/ROTATION on Page level with the meaning of default language/rotation, with the option to overwrite on lower levels and also add an additional attribute OTHERLANGS at Page level as list with all languages found into that document. This additional attribute would also solve https://github.com/altoxml/schema/issues/66. Frederick mentioned a case where on same newspaper page we have both Japanese and English text (different languages and different writing orientation - vertical text, right to left for Japanese) and also Cally mentioned there are a lot of documents where language/rotation can vary on Page level. For these cases, there will be more clarity, since now, LANG/ROTATION are missing on Page level and for the blocks with no setting an arbitrary value can be considered (probably 0 is meaning for ROTATION but for language is not clear at all what is the language if not defined on Block level)

Coordinates related:

https://github.com/altoxml/schema/issues/62 - currently in ALTO we have defined a coordinates system (origin point and measurements unit), but we have no restriction for coordinates (for example do not allow negative values, since top-left corner of the page is always (0,0)). The topic was created some time ago by Jukka after encountering some cases where negative coordinates were found in the ALTO files created by third party tools. A restriction would help to catch these directly via schema validation. Nevertheless, there is still an opened topic, the option to restrict values out of bounds on the other end of the page (block coordinates exceeding page width and/or height), since looks like on schema validation relative restrictions (based on existing values in ALTO file) is not possible. There are ways to do this using SCHEMATRON validation (https://www.schematron.com/) as Thomas mentioned, but not possible on regular xsd validation. Jukka mentioned that these restrictions will break back-compatibility, since older files may became invalid in case these have negative coordinates. Probably we need to take these into account for next major release. Jukka will prepare a schema definition that embed all these changes for future discussion/voting. 

https://github.com/altoxml/schema/issues/49 - this topic is related to polygon shape definition. Currently there is no restriction on how a polygon can be defined, there are multiple valid polygon definitions: "x1 y1 x2 y2 … xn yn" or "x1,y1 x2,y2 … xn,yn" or "(x1,y1) (x2,y2) … (xn,yn)". Keeping this flexibility is ok for back compatibility, but makes it quite difficult for ALTO processors to take into account all possible options. Restricting the values would make ALTO processors work more easier in the future, but will break back compatibility. There were several opinion on this topic during the meeting. Thomas mentioned that back compatibility is an important issue and he would go for keeping this. Art mentioned that this topic was not discussed that much and looks like there is not a high prio topic (was set as high prio in the past, but then the flag was removed due to lack of interest). Due to that and the fact that a change would break back compatibility Art was also in favor of closing the issue. Cally also agree with this. Based on these discussions we propose the topic to be closed. We set it for voting (if agree to close it, please vote with ACCEPT).

Regarding last topic, face-to-face ALTO board meeting, looks like the most promising place would be Alicante, Spain at DATeCH 2022 in December 2022. For DAS 2022 conference is probably too late to organize a meeting, but for the others we can still vote. Even we will organize an ALTO board meeting only on one conference, these conferences could still be a good place to meet each other, for those that will attend.
