# 2019-11-03 ALTO Board Meeting Minutes
**Agenda**
1. Open discussion of encoding OCR uncertainty and alternative hypotheses. [**All**]
2. Other business. [**All**]

**Attending members**

* Raju Buddharaju
* Ciprian Dinu
* Ashok Popat
* Art Rhyno

**Guests**

* Robert Sachunsky

**Minutes**

The Board welcomed Robert, who has made a proposal to support a _lattice_ structure within ALTO as part of contributing to the
[Allow a String to contain alternative Glyph segmentation hypotheses](https://github.com/altoxml/schema/issues/57) github 
issue. Robert described his related work in creating a post OCR correction module within the [OCR-D project](http://ocr-d.de/eng)
and noted the usefulness of lattices for functions like keyword-spotting. 

In response to questions about tools and support for lattices, Robert described [NetworkX](https://networkx.github.io/) as a useful 
library for graph processing in python, and gave some background on the 
[discussion of lattice support for the PAGE format](https://github.com/OCR-D/spec/issues/72). Lattice
support may be more applicable to ALTO given PAGE's focus on ground truth presentation and ALTO's close relationship to OCR. Ashok
noted that the mission of ALTO is compatible with supporting lattices in the sense of capturing all of the information that
the OCR engine has access to.

Ashok gave some background on Google's use of lattices. Internally, Google uses lattices for two different scenarios. One
involving traditional OCR workflows, such as pages from Google Books, and one for scene text, for example, from mobile devices,
where there might be specialized language models, such as if a phone captures a URL text representation. There are cases
where it has been useful to merge OCR results from different engines for better accuracy, and using a lattice structure has 
allowed this to occur.  Cip pointed out the difficulty of dealing with multiple OCR engines in terms of supplying a voting
mechanism or some other process to pick one result over another.

One of the questions arising from the discussion on Glyph segmentation hypotheses was whether more than one confidence score 
was required in the representation, since language models in general need a history of more than one lattice element as input. 
Ashok's colleague, Yasuhisa Fujii, has clarified that Google currently uses a model that is denser than a lattice, more like a 
tree that is expanded as needed. This allows context to be kept before pruning occurs, and a hybrid lattice-tree 
representation preserves state. For lattices in ALTO, it may not make sense to attempt to separate out scores.

Robert gave some details on his proposal, which targets both gylph and word ambiguity. Glyphs become the nodes in the lattice,
and he uses an element called _span_ for the edges ([see example here](/altoxml/schema/issues/57#issuecomment-510266788)). Art 
showed some syntax that combined the _StringVariant_ element with Robert's syntax, but it was agreed that _StringVariant_ 
is a different discusson, and that the lattice proposal should become its own [github issue](/altoxml/schema/issues/63). 

It is recognized that scoring and rescoring OCR with lattices has great potential but can be confusing. Robert noted that newer 
language models need a lot of context for rescoring to be an option. Art asked if the language models in the 
[Kaldi Speech Recognition Toolkit](https://kaldi-asr.org/) are a good source for understanding language models in OCR 
(Kaldi is of interest because of its general purpose lattice tools). Robert suggested that the language models are really 
equivalent, though Kaldi uses an acoustic rather than a visual approach.

Ashok suggested there are scenarios where it might be worth having a record of the relative role
of the language model in scoring. Robert suggested a convention that language model scores always represent the best path
to that point, and maybe the visual score should be what is encoded in ALTO. Art asked whether Google passes on language
model scoring in OCR processing, and Ashok described a workflow where the language model score is the best path in progress as 
opposed to trying to capture more state, and that it is much more difficult to rescore if a language model has already been
applied. Robert's approach has been to work from line to line, and to return traceback of the number of best hypotheses up 
to that point that includes all of the history along with the state vectors of the history.

Another consideration in lattice representation is the granularity of the hypothesis space. Ashok noted that Google has largely 
worked with fully composed unicode characters but has experimented with other possibilities, from fractional characters to byte 
encoding, where each byte has a score. Generally, it is the job of the language model is to provide a prediction possibility of 
the next token conditioned on the probabilty of all previous tokens, but in practice, a sliding window is used to pass tokens. 
Robert's experience is that neural networks can learn UTF presentation quite well, and that this seems to be the most common 
granularity.

It was agreed that the goal is some form of compact representation of multiple hypotheses, with some form of uncertainity, and 
the way to proceed should include testing under different scenarios, including HTR (handwritten text recognition) and RTL 
(right-to-left) languages. Cip and Raju asked about the XML overhead, Robert's example syntax appeared to have duplicate content, 
but IDREFs might be an option if this is a concern. There was some discussion about whether a lattice element would be an optional 
equivalent to _TextLine_ and _String_, a child element, or both. It is the most likely that a lattice would normally represent an
entire _TextLine_ though it might model a partial line. 

With a commitment to sort out the syntax in github, the question turned to sources of test data. This is challenging given that
test data would ideally come from OCR engines which typically don't expose lattice-level information. Ashok will investigate if
any of Google's data can be made available and Robert will check into a colleague's work on expanding tesseract's beam search,
which might offer the prospect of using tesseract to generate test data. 

Art asked if there might be data within the [Transkribus](https://transkribus.eu/Transkribus/) project or if there was any 
potential in the ocropus-era of [ocropy](/tmbdev/ocropy) which supported lattice export. Robert will reach out to _Transkribus_ 
but has looked into _ocropus_ which did not use CNN/LSTM at the time, and would not likely be relevant. _Transkribus_ uses a 
matrix structure instead of a lattice, and the [code base](/CITlabRostock/CITlabConfMat) has been shared with the Board. While 
there may not be any existing OCR engine that could be a source of lattice-specific data, it is possible that demonstrating 
the potential of sharing lattices will encourage more support for exposing this level of detail. Ashok noted that his team's 
use of lattices was initially a consequence of using an HMM-based system that supported lattices, and this led to an 
appreciation of their utility.

Under _Other Business_, Robert asked about the [SP](/altoxml/schema/issues/54) issue, noting the importance of spacing
for using language models, and the ongoing work to establish a standard set of metrics for space identification. The issue
is ongoing but spacing may need special handling for lattice support.
