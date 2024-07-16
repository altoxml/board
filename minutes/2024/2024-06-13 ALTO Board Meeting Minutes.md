# 2024-06-13 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Topics to discuss:
    * Voting status for proposed solution for opened points (changes available on individual branches on git-hub) 
    * ALTO "quality assurance check" - SCHEMATRON definition for detailed checks - original topic: Restrict float attribute values where possible to allow for better xml-validation (https://github.com/altoxml/schema/issues/62) 
        * sample SCHEMATRON definition
        * discuss possible tests we can cover by this (cordinates, other consistencies checks, etc.)  
4. Release date proposals for 5.0 
    * Proposed date
    * What should contain 5.0  
5. Face-to-face meeting proposals: 
    * ICDAR 2024, Athens, Greece, 30th of August - 4th September 2024
    * ICPR 2024, Kolkata, India, 1st - 5th December 2024
6. Other business. [**All**]

**Attending members**
* Cally Law
* Ciprian Dinu
* Hany Abdellatif
* Sebastien Cretin
* Stefan Pletschacher
* Thomas Haighton

**Minutes**
* Brief review of topics for ALTO 5.0 ([67](https://github.com/altoxml/schema/issues/67), [80](https://github.com/altoxml/schema/issues/80), [82](https://github.com/altoxml/schema/issues/82), [72](https://github.com/altoxml/schema/issues/72)) on voting state. More votes and detailed review is needed for topic [80](https://github.com/altoxml/schema/issues/80) - PointsType restrictions. 
* Main topic for today is [62](https://github.com/altoxml/schema/issues/62) - aditional validation/restrictions for values contained in ALTO. Initial proposal was based on xsd 1.1 and use asserts for more complex tests like text right bound to be smaller than page width. This approach, has two inconvenients, force validation with xsd 1.1 and number of free tools is limited for this, and second there is a risk for validation failure for a lot of files, even in practice ALTO processors can go over many of the exceptions presented into item [62](https://github.com/altoxml/schema/issues/62).
* Alternatively, we may split validation into two parts, one mandatory, structural validation (what we usually do with current xsd schema) and an optional part more close to quality assurance (validate negative values, boxes out of bounderies, etc). Those who would like to have a more restrictive check on ALTO files will be able to do this, but this will be optional. As technical solution, a proposal would be to use SCHEMATRON validation for the optional part.
* Beside new ALTO 5.0 schema we may provide and maintain also a SCHEMATRON schema as recommendation for detailed quality assurance.
* Thomas created a first simple sample of SCHEMATRON validation for ALTO and presents it together with a general presentation for SCHEMATRON. SCHEMATRON is based on xslt, both xslt 1.0 and 2.0 could be used, but 2.0 offers more functions and can make the validation rules more powerfull, while it has a weak point, there are not too many open source tools to support 2.0. For presentation Thomas used Oxygen XML Editor as tool, and xslt 2.0.
* In ALTO 5.0 we can add as documentation node the information regarding SCHEMATRON and usage, and keep SCHEMATRON as separate schema.
* Stefan mentioned that in the past the way that these sanity checks were made were basically custom and implemented directly into the aplications that use ALTO as input. Having a more generic way as SCHEMATRON, including a base schema to check all these details would be a much better way to deal with specific sanity checks on ALTO files.
* One question that raises is what tools are available, or how to integrate SCHEMATRON validation in a pipeline. Beside comercial tools (Oxygen, CCS Validator), Saxon java library can be used for SCHEMATRON validation (https://www.saxonica.com/html/documentation12/about/whatis.html). Validation can be done as well using python package lxml, but this supports only xslt 1.0. Ideally would be if we can create SCHEMATRON schema using xslt 1.0 functions, since more tools are available.
* Another idea would be to have also multiple levels of SCHEMATRON validation, like basic checks and then more advanced (sort of classification as error, warning, info). This may help users to select their own conformance level for ALTO files.
* In order to move forward and collect ideas we will create a new topic on github where everybody can post tests ideas. We will start with the simple sample we have now and add more tests based on collected ideas. Ideally would be very useful (specially for people not experts into technical area) to have a sort of catalog, a list with all available tests.
* We should think also on previous versions of ALTO, and have maybe different SCHEMATRON files. For the moment we should focus on a first solution as general as possible, try to prioritize tests that are valid for all versions. Another idea would be check also the version for checks that are version specific.
* Release date for 5.0 was discussed - there are two options, one to have a version sooner, but without all these SCHEMATRON topics (or other new ideas) or delay the release for beginning of the next year, to have a more consistent release. Majority opinion was to delay the release date.
* Would be a good idea to invite new members into ALTO Board from different areas as handwritten text community (Transkribus, eScriptorium) and from presentation systems world that use ALTO (IIIF, Veridian)
* As next face to face meeting place is proposed ICDAR 2024, Athens/Greece 30th August - 4th September or ICPR 2024, Kolkata/India 1st-5th December 2024. Voting available here: https://doodle.com/meeting/participate/id/bo6BB5ka
