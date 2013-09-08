## This page lists known issues to which I have no (elegant) solutions.

### Reflowable Text
[Dedicated page](https://github.com/coolwanglu/pdf2htmlEX/wiki/Reflowable-Text)

### Stroked Text
In PDF, different colors (or transparent) can be specified for outline and inside of text.
 - WebKit supports text-stroke-color & text-fill-color. No problem.
 - For Firefox, text-stroke-color may be simulated by drop shadows in 4 different directions
  - **But how about when fill-color is transparent?**
 - No need to mention IE...

### Text with clipping path
In PDF, a path may be used to limit the visible region. Currently only rectanglar clipping regions are supported by pdf2htmlEX, for other paths, the bounding box will be used.
 - The CSS property `clip-path` may be useful

### Text behind an image
If you put an opaque image over some text in PDF, the text should not be visible at all. But in current design of pdf2htmlEX, all text are 'elevated' to the top level such that all such text will be visible.

### Type 3 fonts
Glyphs in a type 3 font is actually a mini-PDF.
 - How to dump to out
 - Fontforge seems to support type 3 fonts

### Writing mode fonts
Text go top-down, right-left, instead of left-right top-down.
 - HTML supports such fonts?
 - How to position them in HTML?