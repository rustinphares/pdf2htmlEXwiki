##Possible ideas for GSoC 2013

pdf2htmlEX is not a large project, but it involves a number of modern, tasty technologies including
 - Programming Languages: C++, Javascript and a little C and Python
 - Web related: HTML5, CSS3, fonts
 - The PDF format
 - Libraries: poppler, FontForge and jQuery

Should you be familiar with a few in the list, it's very likely that you will find some delicious ideas below:

TBE = To be explained by the mentor: a mentor will give a brief introduction to the topic, and list relative materials for the students to read.

### Support fonts in writing modes
In PDF, text in writing modes are placed top-to-bottom instead of left-to-right. Currently such kind of text are converted into images.

The task is to render text in writing mode natively in HTML. There have been relative CSS properties, but we need to make sure that the characters are placed accurately.

 - Skills required: 
  - CSS, C++
  - understanding the relative parts of poppler, ans possibly also FontForge (TBE)
  - understanding of ascent/descent of a font (TBE)
  - understanding how characters are placed accurately by pdf2htmlEX (TBE)
 - Difficulty: MEDIUM

### Support Type 3 fonts
In PDF, type 3 font is the only one of its kind. Instead of an embeded font file, type 3 font is a series of PDF instructions. In other words, in a type 3 font, each glyph is defined as a "mini-PDF".

The task is to extract Type 3 fonts from PDF and convert into something compatible with HTML. A possible solution is SVG fonts. pdftocairo (from poppler) is doing something similar and should be consulted.

 - Skills required:
  - C++
  - Familiar with poppler, especially the cairo backend
  - Understanding of Type 3 fonts in PDF Spec (TBE)
 - Difficulty: HARD

### Support text with clipping path
In PDF, a clipping path,e.g. a circle, defines the visible area, everything outside the area will not be rendered. Currently pdf2htmlEX ignores all the clipping path.

The task is to recognize the clipping paths, fully visible text are still rendered as they were, fully invisible text should be ignored, and partially visible text should be converted into images (or maybe better ways)

 - Skills required:
  - C++
  - Basic understanding of the clipping path (TBE)
  - Understanding character placement in pdf2htmlEX (TBE)
 - Difficulty: MEDIUM

### Reduce the size of background images
Currently for each PDF page, pdf2htmlEX will render everything it cannot handle into a large canvas, which might leads to a very large image file.

The task is to optimize the size, for example small pieces should be recognized such that a number of small images will be produces instead of a single large one. Clipping path should be taken into consideration.

 - Skills required:
  - C++
  - Understanding of drawing, image and clipping path in PDF (TBE)
  - Understanding of relative API of poppler (TBE)
 - Difficulty: HARD

### Automated tests
pdf2htmlEX is changing all the time, and we need to prevent regressions.

The task is to build an automated regression tests, which had better to be integrated with Travis CI. The image-based regressions test from PDF.js is a good reference. [This link](http://acroeng.adobe.com/wp/) provides a number of test cases.

 - Skills required:
  - Python and relative modules (HTML to image conversion (better with Webkit/Gecko) & image comparison) 
 - Difficulty: EASY

### Improve the default UI
Currently the default UI barely combines the pages, which is not attractive.

The task is to add more necessary & useful UI elements, e.g. pageup/down buttons, and features, e.g. lazy page loading with Ajax.

 - Skills required:
  - Javascript
  - Basic understanding of the structure of HTML files produced by pdf2htmlEX (TBE)
 - Difficulty: EASY

### Text flow detection
Text in almost all PDF files are absolute positioned, which means they cannot be adjusted automatically if the width of the viewer is changed. However text reflowing is quite natural in HTML. [This link](https://github.com/coolwanglu/pdf2htmlEX/wiki/Reflowable-Text) shows why it's not easy to make text in PDF reflowable.

The task is to find a solution and implement it.

 - Skills required: 
  - C++ 
  - Understanding how text are extracted and handled by poppler and pdf2htmlEX (TBE)
  - Find a solution
 - Difficulty: HARD