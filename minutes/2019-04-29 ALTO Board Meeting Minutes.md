# 2019-04-29 ALTO Board Meeting Minutes
**Agenda**

Special Single Topic Meeting
* [Confidence value calculation (CC - WC - PC) - annotation extension](https://github.com/altoxml/schema/issues/23) [**All**]

**Attending members**
* Ashok Popat
* Art Rhyno
* Cally Law
* Evelien Ket
* Frederick Zarndt
* Hany Abdel Hamid Elsawy
* Joachim Bauer 
* Jukka Kervinen
* Raju Buddharaju
* Stefan Pletschacher

 **Minutes**

Jo gave an introduction to the issue:
   * clients were asking about the meaning of the confidence values in ALTO
   * schema annotation proposed on issue based on _docWorks_ workflow involving multiple OCR engines

Ashok described the process used at Google, where values are calculated in terms of contributions to the confidence error 
rate. A prediction that a character or region has contributed significantly to the error rate, based on a machine-learning 
regression model, has been found to be internally useful.

Stefan reiterated the point made at the last Board meeting that specifing how the confidence value is calculated is probably 
neither realistic or advisable. He outlined what he saw as the three main options on the issue:

   * the schema could prescribe a method or algorithm for calculating confidence
   * the schema could allow any value as long as it is ordered within a specified range, maybe require the value to be linear 
   but not define an equation for its determination
   * the schema could have no constraints at all on the value, but instead rely on a reference to documentation on the 
   algorithm or processing steps leading to the calculation

There was consensus that it is unlikely OCR providers could be convinced to change their internal processes for calculating 
confidence, but that regardless of the source of the values, the numbers for confidence should still have utility. Ashok noted that 
there are approaches that allow some evaluation of confidence externally, for example, reference translations of OCR content that 
can be compared to the confidence levels supplied by the OCR engine. Frederick pointed out the current difficulties of evaluating 
collections with varying confidence numbers from varying engines. 

Ashok suggested there is middle ground between specifying an algorithm and defining what the confidence value is capturing. Stefan 
used the example of 0.8 confidence number from both Abbyy and Tesseract, where the proximity to 1.0 should indicate a strong 
probability of an accurate value irrespective of how it has been calculated. He also noted that adding references to documentation 
on values in XML is well-established in XML schemas, for example, the way that data types are defined in XSD. Ashok asked if 
confidence is as fundamental to OCR as constructs like the definition of bounding boxes and the use of unicode. The need to be crisp 
in notions of comparability and evaluation is important in guiding the discussion on confidence values going forward.

Jo pointed out that there can be wide variance in confidence value calculation depending on which aspect of OCR is being examined. For 
example, word confidence can be greatly impacted by the use of dictionaries, and some aspects of text processing, such as manual 
correction to an OCR value, should be recorded. Art noted that dictionaries can be problematic in some languages where there is not 
necessarily agreement on the spelling. 

There was general agreement that a crucial step is for the Board to decide on which of the options outlined by Stefan should be 
supported by ALTO, and that a google doc might give a bigger canvas for the Board to flesh out the options before adding to the 
github issue and seeking additional feedback. Ashok offered to create the google doc and Art will share the recording of the meeting. 

It was felt that a discussion on the use of dictionaries would be instructive. Art and Frederick both flagged the inconsistent scales 
within ALTO for confidence as a problem, and Ashok asked if it is possible that the use of dictionaries is not necessarily strongly 
related to OCR. For example, a dictionary might be used downstream or outside of an OCR process for evaluation or correction. 

Jo raised some problematic aspects of utilizing dictionaries in OCR, for example, a shorter word is more likely to be misidentified. 
Stefan noted that on a technical level, OCR tends to focus on individual characters, but that discussions on OCR tend to bring in 
broader areas of text processing and document analysis. Hany pointed out that OCR engines that use dictionaries may have different 
capabilities depending on the language, using the example of Abbyy for recognition with Arabic. Jo suggested that an attribute for 
a dictionary as well as one for the type of dictionary might be useful, and that _docWorks_ users might employ several dictionaries 
for text processing, including custom ones.

Frederick noted that words like placenames often come from different sources than a traditional language dictionary when manual 
correction of OCR is being carried out, and described some work he did on evaluating OCR correction from users of the _Veridian_ 
system where the accuracy rate was consistently over 99%. Jukka asked how manual corrections should fit into processing history and 
Jo suggested there might be need for extending the schema, he will add some examples of processing history and what the changes might 
look like to the google doc. The use of manual corrections and how processing is reflected in ALTO dovetails nicely with the 
upcoming face-to-face meeting on handwriting at [DATeCH](http://datech.digitisation.eu/), since it is likely that 
handwriting recognition encoded in ALTO will have even more need than the OCR of typeset text for manual editing and correction.
