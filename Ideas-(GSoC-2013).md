pdf2htmlEX is not a large project, but it involves a number of modern technologies including
 - Programming Languages: C++, JavaScript, some C and Python
 - Web technologies: HTML5, CSS3, fonts
 - The PDF file format [PDF](http://wwwimages.adobe.com/www.adobe.com/content/dam/Adobe/en/devnet/pdf/pdfs/PDF32000_2008.pdf)
 - Libraries: Poppler, FontForge, and jQuery

Should you be familiar with a few in the list, it's very likely that you will find some ideas below:

TBE = To be explained by the mentor: a mentor will give a brief introduction to the topic, and list relative materials for the students to read.

## Support Vertical Writing Mode (CJK)
In PDF, text in vertical writing mode are placed top-to-bottom instead of left-to-right. Currently such text is converted into images.

The task is to render text in vertical writing mode natively in HTML. There are [relevant CSS properties](http://dev.w3.org/csswg/css3-writing-modes/), and we need to make sure that the characters are placed accurately.

 - Skills required: 
  - CSS, C++
  - understanding the relative parts of poppler, and possibly also FontForge (TBE)
  - understanding of ascent/descent of a font (TBE)
  - understanding how characters are placed accurately by pdf2htmlEX (TBE)
 - Difficulty: MEDIUM

## Support PostScript Type 3 fonts
PDF supports a unique kind of font: PostScript Type 3. Instead of an embeded font file, a Type 3 font is a series of PDF instructions. In other words, each glyph is defined as a "mini-PDF".

The task is to extract the Type 3 fonts from PDF and convert them into something compatible with HTML. A possible solution is SVG fonts (though not for all browsers). `pdftocairo` (from Poppler) is doing something similar and should be consulted.

 - Skills required:
  - C++
  - Familiar with Poppler, especially the Cairo backend
  - Understanding of PostScript Type 3 fonts in PDF Spec (TBE)
 - Difficulty: HARD

## Support text with clipping path
In PDF, a clipping path,e.g. a circle, defines the visible area, everything outside the area will not be rendered. Currently pdf2htmlEX does not take into account the clipping path.

The task is to identify the clipping paths, and ensure that fully visible text is rendered, while fully invisible text is ignored. Partially visible text can be be converted into images (unless there are better options).

 - Skills required:
  - C++
  - Basic understanding of the clipping path (TBE)
  - Understanding character placement in pdf2htmlEX (TBE)
 - Difficulty: MEDIUM

## Reduce the size of background images
Currently for each PDF page, pdf2htmlEX will render everything it cannot handle into a background image, which can lead to large image dimensions, and thus large file sizes.

The task is to optimize the background image dimensions, so that multiple smaller images are used in place of a single large background image. The clipping path should be taken into consideration.

 - Skills required:
  - C++
  - Understanding of drawing, image and clipping path in PDF (TBE)
  - Understanding of relative API of poppler (TBE)
 - Difficulty: HARD

## Create automated tests
pdf2htmlEX is changing all the time, and we need to prevent regressions.

The task is to build automated regression tests, which are to be integrated with Travis CI. The image-based regression test from [PDF.js](http://mozilla.github.com/pdf.js/) is a good reference. Adobe have [a large suite of test PDF files](http://acroeng.adobe.com/wp/).

 - Skills required:
  - Python and related modules (HTML to image conversion (better with Webkit/Gecko) & image comparison) 
 - Difficulty: EASY

## Improve the default UI
The default UI is minimal and could easily be improved.

The task is to add more necessary and useful UI elements, e.g. pageup/down buttons, and features, or lazy page loading with AJAX.

 - Skills required:
  - JavaScript
  - Basic understanding of the structure of HTML files produced by pdf2htmlEX (TBE)
 - Difficulty: EASY

## Reflow Text
Text in almost all PDF files are absolute positioned, which means it cannot be adjusted automatically if the width of the viewer is changed. However text reflowing is quite natural in HTML. But [it's not easy to make text in PDF reflowable](https://github.com/coolwanglu/pdf2htmlEX/wiki/Reflowable-Text). Some sort of analysis of the reading order of the document will be required, see [Document Layout Analysis](http://en.wikipedia.org/wiki/Document_Layout_Analysis)

The task is to find a solution and implement it.

 - Skills required: 
  - C++ 
  - Understanding how text are extracted and handled by poppler and pdf2htmlEX (TBE)
  - Find a solution
 - Difficulty: HARD