# 2023-08-23 ALTO Board Meeting Minutes
1. Welcome [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Topics to discuss:
       * Major feature proposal for 5.0: in preparation please provide on github at least one topic/idea to be discussed. Few direction we may explore:
         * How to better support handwritten materials
         * Better support for atypical materials: music scores, scietific books (mathematics, chemistry, physics, electonics, engineering, etc.), old registers with records (commercial, civil, etc), comics, etc.
         * Support for presentation systems that support editing of text information (keep original and edited text maybe)
         * Any other idea, no matter how strange it may sound
4. Other business. [**All**]

**Attending members**
* Ashok Popat
* Cally Law
* Ciprian Dinu
* Clemens Neudecker
* Frederick Zarndt
* Hany A. Elsawy Abdellatif
* Raju Buddharaju
* Jukka Kervinen
* Sebastien Cretin

**Minutes**
* Main topic is related to new features we may add into 5.0.
* One of the proposal was related to the option to enrich content description with more semantic information, for example beside the image (pixels) of a formula to add the formula description in a domain specific xml format (MathML in this case).In general would be an idea to extract semantic information encoded into various graphical components of an illustration, as it was initially intended. We may recover a representation that could have been used for authoring and use the representation to edit again the document for example. Other use case might be to have a sort of illustration description, beside the pixel information. Other idea/example was to be able to add more information to be used on clasification later on, like for a stamp to add more metadata regarding provenience, manufacturer, period, etc. Clemens mentioned that maybe we may have a look on other formats like TEI that provide more descriptive information, rather than pixel level details. On libraries level there are more and more requests to have descriptions like on TEI where is possible to reconstruct the document on semantic level, rather then presenting it as a pixels collection. One important aspect is to be able to describe what Raju mentioned as context, so that any ALTO parser/interpreter to know how to process that part (f.e. if are music scores, to be able to play it based on description, if is complex chemical formula to be able to interpret and render the proper formula based on description). Another question is if we should have a fixed vocabulary for all possible custom descriptions, or would be better to let this free, allowing any content while the reference to a schema is present. As a first step before deciding this would be to collect as many as possible use cases when such additional description makes sense (like mathML, MusicML, etc.). When discussing about tags in ALTO we figure out that in fact now is possible to add additional content like proposed into existing tags. We have "OtherTag" and as "TagType" mainly any xml data can be added. On the other hand, it looks like this is a feature not really used, either because is not clear how to use, or because was not considered useful. Often LayoutTags are used, either to clasify a block, or to mark for example illisible text (at BnF is used like this). StructureTags and NamedEntityTags are maybe not that often used and OtherTags, with complete xml description nobody recall an use case.
* Sebastien open the topic of handwritten text and the need to have content on any level, not only on string level. On previous meeting we discussed about differences between PAGE and ALTO (PAGE being prefered in "handwritten" text processing world) and main difference was the usage - ALTO is mainly used to present the extracted content while PAGE is more used as a tool for preparing groundtruth data for handwritten text recognition. Since on handwritten text recognition text lines looks to be more relevant than words, and most of the engines recognize text on line level, PAGE allows content on any level. Also PAGE is more or less "manually" created and handles more by researchers and flexibility was prefered against consistency, while for ALTO consistency is more important. One particular problem is related to content syncronization on different levels - alowing text content on multiple level is hard to ensure that the text on line level is the same with the text constructed from word level strings. On the other hand there are different HTR engines that generate the text from handwritten material on line level and then artificially split this into word tokens, and this leads to some issues into the final ALTO output. As a solution for consistency problem, Sebastien propose to restrict text content to only one level - for example if text is present on textline level, schema should disallow text on words level. This leads to other issues as well - word coordinates in ALTO are used mainly for highlighting searched words in a presentation system - if text will be only present at line level, the only chance to highlight the words would be by creating artificially estimated coordinates, but as Clemens mentioned, users are not very happy with such solutions. As Sebastien mentioned on research level approaches that extract the text without prior segmentation are present more and more and probably this might be the future approach for text recognition. Having text on line level might be inline with these approaches.
* Frederick asked how confidence information is computed for handwritten text. Sebastian mentioned that mainly this is not something to trust since it gives more indications on maximum capabilities of the used model rather than a real confidence.
* Other discussed topic was related to Arabic text, what could be useful for this language when talking about ALTO.One idea was related to writer information/identification specially for handwritten text. For this tags could be used. Similar information that may be captured in ALTO might be the printer manufacturer, type/class of font (f.e. for Gothic text there are several known styles), etc. Hany presented one of the projects he is working on regarding Arabic manuscripts. The problems outlined are related to segmentation mainly (marginalia texts for example) and also on choosing automatically the right model for prediction based on a writer identification (every writer has his own particularities and dedicated models could be more accurate).
* Ashok mentioned an idea to think of in the future - how we could combine ALTO explicit representation with implicit representation learned by an AI engine that learns "everything" about a particular domain and how this could change ALTO "mission" in the future.  
