# 2024-01-18 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
    * Voting for proposed solution for opened points (changes available on individual branches on git-hub) 
      * Use of LC xlink instead of w3c xlink fails in mixed validation. Mixup/clashes in schema definitions (https://github.com/altoxml/schema/issues/67) - remove xlink, announced on schema 4.4
      * Restrict PointsType to a well defined format (https://github.com/altoxml/schema/issues/80) - implement restrictions defined in  (https://github.com/altoxml/schema/issues/49)
      * Deprecate and then remove ZORDER/IDNEXT since from 4.3 we have a different mechanism for order (https://github.com/altoxml/schema/issues/82) 
      * CC attribute to be deprecated (https://github.com/altoxml/schema/issues/72)
    * Most important change - decide the direction (force xsd 1.1 validation for 5.0, or impleent partially issue 62)
      * Restrict float attribute values where possible to allow for better xml-validation (https://github.com/altoxml/schema/issues/62)  
4. Major feature proposal for 5.0:
    * Topics proposed:
      * Text on line level, not only on string level 
      * Enriching ALTO with more details domain specific (mathematical formula description, music scores, electronic schemas, chemical formulas)
      * Illustration descriptions (maybe automatically illustration tagging)
    * Any new idea is welcomed!  
5. Face-to-face meeting new proposal: probably ICDAR 2024, Athens, Greece, September 2024?
6. Memberships expired end of 2023 - intention to continue/stop
7. ALTO Chair - two years mandate expired - extend/new candidates 
8. Other business. [**All**]

**Attending members**
* Ashok Popat
* Brian Geiger
* Cally Law
* Ciprian Dinu
* Raju Buddharaju
* John Loitzenbauer
* Jukka Kervinen
* Stefan Pletschacher

**Minutes**
* The meeting started with a review of changes proposed for 5.0 that break back compatibility. First topic was related to xLink atribute that creates in the past several issues. There were two proposals to fix this topic - one was to add our own attributes group (inspired by METS board proposals for similar issue) and second was to completely remove the attribute since is not used in practice, at least from our knowledge. For voting was proposed in the end the last one, remove xLink attributes group from schema
* Second topic was related to PointsType restriction. Proposed regular expression was presented and voting was opened for the topic. 
* Third topic was related to former way of defining order in ALTO (IDNEXT) that currently enter in a conflict with last changes from 4.3. Instead of defining how to interpret conflicting situations (who has a higher priority, older or newer system) proposal is to simply remove the previous way of order definition (IDNEXT attribute)
* Last topic for voting was related to CC attribute. In the past there was a proposal to remove CC attribute while Glyphs could be used to provide details on character level, including confidence. In practice glyphs were not used that much and CC remains the best way to express confidence on character level. Proposal was to make no change on this attribute
* Stefan pointed out that the way we record the changes is not that accurate in the case of CC attribute - the title of the topic is "Deprecate CCS attribute" while the answers are all "ACCEPT" and this is confusing without reading the entire thread. One idea is to change the status to "Reject" before closing. Another idea could be to syncronize the title of the topic with the actions. 
* The last topic that break compatibility is related to restriction of float values attributes, not only on fixed values/ranges but also restrict values based on ALTO file content itself. This is possible only using XSD 1.1. There are few ways to continue with this topic. One is simply discard the request, second is to use simple but incomplete rules like having positiv values, or values in a fixed range, and still be compatible with XSD 1.0 processors, or fully implement restrictions, but then from 5.0, XSD 1.1 processors will be needed
* Stefan mentioned that even for software developers such restrictions would make things simpler, in practice there are many cases when ALTO files fails to comply with these restrictions and there are always reasons for this. Such restrictions would force the users to go back and find the roots of the problem and fix it, while a practical approach where these exceptions can be accepted is desired (or much less "painfull"). Would be good if is possible to split the validation issues into two categories, one related to structural correctness of the format means to ensure that the ALTO file can be ingested in an application, and second category of issues more on the logical side (not to have coordinates out of page, etc). 
* One idea could be to not add this restriction to schema, but come with additional SCHEMATRON validation rules, as add-on for those that would like more detailed validation, on logical level. Stefan proposed to try to validate with a library, or other real life users and validate a collection to see how often a very restrictive validation will fail.
* Ashok mentioned that beside the validation itself would be important to understand how easy would be to create some "convertors" that automatically fix the issue (f.e. bring an angle always in range 0-360 degree if this is the restriction and angles are in range -180 to 180 degrees). For this a validation in real world would be needed, to understand what are the issues that appear more often and what solutions might be to fix them. To find a generic tool to "fix" automatically "all" issues caused by the restrictions might be quite challenging. The conclussion is that we need some time to experience with a pre-release version, or a trial version and then revisit this topic
* Stefan mentioned that with this new topic we go more into quality assurance teritory (for that, there are some tools of "validator" type, that not only validates the schema as of today, but goes more in detail and check different other aspects, more like completness tests). We would probably need to have an extended specification and if somebody would like to use that, to have the needed tools, else it still should be possible to perform a sort of basic validation via schema. We should check is assertions in XSD 1.1 can be enabled or disabled, then we might combine everything into one single schema
* Other features proposed on the last meeting were discussed - textline level text, not only on string level. One proposal was to have the option for text to be stored on text line level, but in this case completely disable anything bellow. In this way we get rid of possible inconsistencies between two text versions. On PAGE text is allowed on both levels, with no restrictions, since it looks more convenient, but if this is a good practice or not, is not quite clear. Maybe if we will use assertions on validation, or SCHEMATRON, we may check this as quality assurance step, but do not enforce this by default. Stefan mentioned that would be good to find some hand written text specialists into ALTO board. Ashok mentioned he may check at Google and try to bring one of his colleagues into the board. 
* Two more topics were revisited - the option to describe the content using domain specific definitions (means embed in ALTO files xml descriptions according with other schemas like MathML for formulas of MusicML for music scores) and also the option to attach a description to an Illustration, specially that now there are a lot of tools that can make this automatically. 
* For domain specific definitions, the original topic proposed a way to define this, but in fact this can be done using tag definitions in ALTO. What is missing in fact is a documentation and some samples on how this can be done.
* In order to collect more usage cases and understand the users needs would be good to check if we can get some statistic information of what is used and what not, and also involve presentation systems providers that really use ALTO (like Veridian, or IIIF)
* Organisatoric topics: 
* The current members are ok to continue for the next two years, Ashok mentioned he will check if somebody from Google, more technically involved can join the board
* As Chair role Cip will continue for the next two years, but after four years might be more beneficial for ALTO board to have a change
* As next face to face meeting place is proposed ICDAR 2024, Athens/Greece 30th August - 4th September.
