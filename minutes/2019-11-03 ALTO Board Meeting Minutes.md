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

In response to questions about tool and library support for lattices, Robert described [NetworkX](https://networkx.github.io/) as a useful 
library for general graph processing in python, 
and mentioned there are various implementations like [OpenFST](http://www.openfst.org/) for finite-state transducers.
He also gave some background on the 
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

One of the questions arising from the discussion on lattice representation was whether more than one confidence score 
would be useful in the representation, since language models allow rescoring, and keeping OCR and LM scores separate would facilitate attributing the blame afterwards.
However, as Robert pointed out, LM in general need a history of more than one lattice element as input, so each score is necessarily relative to the path it came from. 
Without a chance to represent the LM scores directly in the lattice, therefore it is only during the rescoring process (as an in-memory focal point) that both contributions can be adequately weighted against each other.
In consequence, according to Robert, it does not make sense to preserve both scores afterwards.

Ashok then objected that it could still be useful to preserve the LM score of each lattice element in the single-best path up to that element during rescoring. This still enables some diagnostics over local relative strengths between OCR and LM contributions.
Ashok's colleague, Yasuhisa Fujii, has clarified that Google currently uses a model that is denser than a lattice, more like a 
tree that is expanded as needed. This allows context to be kept before pruning occurs, and a hybrid lattice-tree 
representation preserves state. For lattices in ALTO, it may not make sense to attempt to separate out scores.

Robert then gave some details on his proposal, which targets both gylph and word segmentation ambiguity at the same time. Glyphs become the nodes in the lattice,
and he uses an element called _Span_ for the edges which merely reference the Glyphs to be connected ([see example here](https://github.com/altoxml/schema/issues/63#issuecomment-550991423)). Both sets of elements are then subsumed over a _Lattice_ element.

Art subsequently showed some syntax that combined the new _StringVariant_ element with _Lattice_, 
but Robert objected that not allowing the lattice to contain independent nodes would restrict the graph to a (linear/totally ordered) confusion network structure again, which _Lattice_ set out to overcome in the first place.
However, _StringVariant_ being a natural token-level analogue to _Variant_ on the glyph-level, it was agreed this
is a different discusson, and that the lattice proposal should become its own [github issue](https://github.com/altoxml/schema/issues/63). 

It is recognized that scoring and rescoring OCR with lattices has great potential but can be confusing. Robert noted that newer 
language models need a lot of context (beyond a single line) for predictions to become accurate. Art asked if the LM rescoring in the 
[Kaldi Speech Recognition Toolkit](https://kaldi-asr.org/) is a good example for understanding LM rescoring in OCR 
(Kaldi being of interest because of its efficient FST implementation). Robert suggested that the language models are really 
equivalent, though ASR uses an acoustic rather than an optical model to create the input lattice.

Ashok suggested there are scenarios where it might be worth having a record of the relative role
of the language model in scoring. Robert suggested a convention that language model scores always represent the best path
to that point, and maybe the visual score should be what is encoded in ALTO. Art asked whether Google passes on language
model scoring in OCR processing, and Ashok described a workflow where the language model score is the best path in progress as 
opposed to trying to capture more state, and that it is much more difficult to rescore if a language model has already been
applied. Robert's approach has been to work from line to line, and to return traceback of the number of best hypotheses up 
to that point that includes all of the history along with the state vectors of the history.

Another consideration in lattice representation is the granularity of the hypothesis space. Ashok noted that Google has largely 
worked with fully composed Unicode characters (grapheme clusters) but has experimented with other possibilities, 
from codepoints to bytes, where each byte has a score. Generally, it is the job of the language model to predict the probability of 
the next token conditioned on the probabilty of all previous tokens (whatever granularity level for tokens may be), but in practice, a sliding window is used to pass tokens. 
Robert's experience is that neural networks can learn UTF presentation quite well, but that using characters seems to be the most common granularity and can be equally flexible when using "open vocabulary" schemes.

Cip and Raju asked about the XML overhead of the lattice representation, since Robert's example syntax appeared to have duplicate content and the OCR search space can be very large. 
But _Span_'s IDREFs can reference existing Glyphs were available, and the whole lattice can always be pruned prior to representation.

There was some discussion about how to make the lattice extension fully optional in order to avoid the burden of graph processing for implementors.
In the proposed scheme, _Lattice_ would have been optional for the producer of annotation, but obligatory for the consumer.
Cip came up with the solution of not allowing _Lattice_ interchangeably with _String_ within _TextLine_, but keep it separate from the _String_ and _SP_ sequence (and always representing an entire line), and possibly also allowing _Lattice_ as a child of _String_ after the  _Glyph_ sequence (representing local ambiguity).
Thus, on both levels, the old representation would become but the best path of the lattice in the new representation, the latter being fully optional to producer as well as consumer of annotation.
Normally, OCR ambiguity would have to be represented for an entire _TextLine_, though it might also model a partial line. 

It was agreed that the goal is some form of compact representation of multiple hypotheses, with some form of uncertainity, and 
the way to proceed should include testing under different scenarios, including HTR (handwritten text recognition) and RTL 
(right-to-left) languages. 

With a commitment to sort out the syntax in github, the question turned to sources of test data. This is challenging given that
test data would ideally come from OCR engines which typically don't expose lattice-level information. Ashok will investigate if
any of Google's data can be made available, and Robert will check into a colleague's work on expanding Tesseract's beam decoder width for the feasibility in his lattice output prototype, 
which might offer the prospect of using tesseract to generate test data. 

Art asked if there might be data within the [Transkribus](https://transkribus.eu/Transkribus/) project or if there was any 
potential in re-activating lattice support in [Ocropus](/tmbdev/ocropy) `OLD/`. Robert will reach out to _Transkribus_ 
but has looked into _ocropus_ which did not use CNN/LSTM at the time, and would therefore not be relevant. _Transkribus_ uses a 
matrix structure instead of a lattice, and the [code base](/CITlabRostock/CITlabConfMat) has been shared with the Board. While 
there may not be any existing OCR engine that could be a source of lattice-specific data, it is possible that demonstrating 
the potential of sharing lattices will encourage more support for exposing this level of detail. Ashok noted that his team's 
use of lattices was initially a consequence of using an HMM-based system that supported lattices, and this led to an 
appreciation of their utility.

Under _Other Business_, Robert commented on the [SP](https://github.com/altoxml/schema/issues/54) issue, noting the importance of explicit spacing
for using language models, and the close relation of the lattice issue to the question raised by the SP issue of whether the _String_ sequence is allowed to be interpreted out-of-order and with overlapping coordinates.
If that was the case, then word segmentation ambiguity would already be representable as is, without the need for a lattice extension. The issue is ongoing but spacing may need special handling for lattice support.

Ashok added that white space is practically considered as characters in OCR processing nowadays, but that spacing can then become an issue with CER evaluation.
Robert replied that standard Levenshtein distance is not only unfair to different types of white space but to other semantically close groups of characters as well, especially for historic texts.
This can be seen as part of the ongoing work to establish a standard set of metrics more suitable to different application scenarios.
