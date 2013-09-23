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

### Writing mode fonts
Text go top-bottom, right-left
 - HTML supports such fonts?
 - How to position them in HTML?
   - CSS rule `writing-mode` is not yet well supported.

### Font size rounding by browsers
10.3pt text are usually rendered as 10pt text in web browsers, which often causes inaccuracy in the layout.

Relative links:

- http://meyerweb.com/eric/thoughts/2010/02/10/rounding-off/
- https://developer.mozilla.org/en-US/docs/Web/CSS/text-rendering