## This page lists known issues to which I have no (elegant) solutions.

### Reflowable Text
[Dedicated page](https://github.com/coolwanglu/pdf2htmlEX/wiki/Reflowable-Text)

### Printing
[Dedicagted page](https://github.com/coolwanglu/pdf2htmlEX/wiki/Printing)

### Text outline
In PDF, different colors (or transparent) can be specified for outline and inside of text.
 - WebKit supports text-stroke-color & text-fill-color. No problem.
 - For Firefox, text-stroke-color may be simulated by drop shadows in 4 different directions
  - **But how about when fill-color is transparent?**
 - No need to mention IE...

### Text with clipping path
In PDF, a path may be used to limit the region of display, which is not supported in HTML/CSS
 - At least detect if the text is visible, if not, don't show it in HTML (Working in progress).
 - When the clipping path is a rectangle, may use a <div> to simulate, slow ?
 - To render them in the background image, and create a hidden text layer on top of it (like PDF.js)

### Type 3 fonts
Glyphs in a type 3 font is actually a mini-PDF.
 - How to dump to out
 - Fontforge seems to support type 3 fonts

### Writing mode fonts
Text go top-down, right-left, instead of left-right top-down.
 - HTML supports such fonts?
 - How to position them in HTML?
