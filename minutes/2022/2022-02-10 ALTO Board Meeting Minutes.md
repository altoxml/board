# 2022-02-10 ALTO Board Meeting Minutes
1. Welcome - with special guests [Benjamin Kiessling](https://github.com/mittagessen) and [Robert Sachunsky](https://github.com/bertsky) [**All**]
2. Find and tell a non-offensive, maybe self-deprecating joke before the meeting begins and/or after it ends. [**All**]
3. Continue discussion of _Schema Pull Request_ - [Direction, orientation, and reading order (text direction elements) #74](https://github.com/altoxml/schema/pull/74) and prepare for voting. [**All**]
4. Upcoming Board Expirations:
   * _December 31, 2021_: Frederick, Nate, Matthew, and Ahmed Samir - update status
   * Update the members list and expiration
5. Next face-to-face meeting proposals:
   * DAS 2022, La Rochelle, France (https://das2022.univ-lr.fr/) (22-25.05.2022)
   * ICFHR 2022, Hyderabad, India (http://icfhr2022.org/) (December 2022)
6. Other business. [**All**]

**Attending members**
* Raju Buddharaju
* Sebastien Cretin 
* Ciprian Dinu
* Hany Abdel Hamid Elsawy 
* Brian Geiger 
* Thomas Haighton
* Jukka Kervinen
* Cally Law
* Clemens Neudecker
* Ashok Popat
* Art Rhyno
* Frederick Zarndt

**Participating guests**
* Benjamin Kiessling
* Robert Sachunsky

 **Minutes**

Ben briefly explained latest changes made regarding today’s main topic (pull request Direction, orientation, and reading order (text direction elements) #74), based on last meeting discussion and ideas. Some examples were added to better explain the usage of Reading Order and as well additional documentation was added inside ALTO schema. Samples can be found on https://github.com/mittagessen/alto_ro_examples . One example was related to newspapers – mainly a conversion from a PAGE example to ALTO plus needed adaptation, and there are two more examples based on more complex cases from Hebrew manuscripts. Documentation was updated as well – originally the documentation was done considering that users are familiar with intrinsic Unicode characters reading order. Updated documentation clarifies possible confusions and also provide a link to W3C document that explains in detail writing modes (https://www.w3.org/TR/css-writing-modes-3/#writing-mode) on InlineDirType definition.

Cip asked if would make sense to create a version 5.0 instead of 4.3, since the proposed feature is a consistent one. Since the backward compatibility is not affected, and the rule state that major version will be changed only in this case, it was decided to go for 4.3. Cip proposed to prepare the solved topics for voting, Ben mentioned that from his perspective topic covers all the aspect. Ben mentioned he will also modify the changes log, last remaining thing before voting. 

Clemens and Ben mentioned about the change that was in discussion that could break the backward compatibility – removing CC attribute, and since this will not be added into the next release, we can remain with version 4.3. 

Cip proposed not to add other features on this new version, so that we can release faster a new version while many people wait for reading order topic clarification. This new version solves three opened issues ([#18](https://github.com/altoxml/schema/issues/18), [#68](https://github.com/altoxml/schema/issues/68), [#73](https://github.com/altoxml/schema/issues/73)). Clemens proposed also to include ([#71](https://github.com/altoxml/schema/issues/71)) since is a simple typo change. Ben and Clemens mentioned as well that this change is waited into community and a version solving only this topic is desired. Ben asked for a time line and also asked if there is needed another meeting for voting. Proposed time line for releasing the version was March 2022 and the voting procedure was clarified (by adding a comment into the topic to be voted). Clemens proposed to send out an announcement to the community before releasing the new version to collect feedback to proposed changes. Frederick mentioned about existing mailing list that may be used for this.

Ben provided additional information regarding the examples provided. 

Robert manages to join at the end of the meeting and he also mentioned the proposed changes are ok. 

There were several discussions regarding the documentation, on how we could provide examples for each new feature we add into ALTO schema. Cip proposed a link into documentation strings or change log to the provided samples. Everybody agreed with the need of better documentation by samples (including easy to understand visual representation of both image and ALTO layers). There is currently an examples repository but, in many cases, only ALTO files are present and is hard to understand the samples. One use case created in the past by Evelyn was mentioned as a good practice. Is important to have a good visualization. This topic worth to be added as long-term topic for ALTO board.

Organizational topics:

Expired membership: Frederick, Nate, will continue; Mattew will not continue probably; need confirmation from Ahmed Samir

Face-to-face meeting: There were two initial proposals:
*	DAS 2022, La Rochelle, France (https://das2022.univ-lr.fr/) (22-25.05.2022)
*	ICFHR 2022, Hyderabad, India (http://icfhr2022.org/) (December 2022)
There were two additional proposals:
*	ICPR 2022, Montreal, Canada (https://www.icpr2022.com/) (21-25.08.2022) 
*	DATeCH 2022 – not set yet for sure, intention to be organized, probably in Florence, Italy

Cip will prepare a survey to see what would be the main choice for face-to-face meeting.

Art proposed as his replacement John Loitzenbauer from Canadiana project (www.canadiana.ca) and opened e-mail voting procedure.
Another opened topic was related to used platform for meetings, since Zoom created some issues at least on this meeting. There were some alternative proposals mentioned (Teams, BigBlueButton, Jitsi). For the moment we will keep using Zoom, but maybe on long term other options might worth.
