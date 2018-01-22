## This page lists known issues to which I have no (elegant) solutions.

### Reflowable Text
[Dedicated page](https://github.com/pdf2htmlEX/pdf2htmlEX/wiki/Reflowable-Text)

### Stroked Text
In PDF, different colors (or transparent) can be specified for outline and inside of text.
 - WebKit supports text-stroke-color & text-fill-color. No problem.
 - For Firefox, text-stroke-color may be simulated by drop shadows in 4 different directions
  - **But how about when fill-color is transparent?**
 - No need to mention IE...

### Clipped or overlapped text
Text in PDF may be partially clipped, or completely invisible due to being overlapped by another object (e.g. an image). But they may appear visible in the output of pdf2htmlEX. The reason is that currently pdf2htmlEX uses a single background image behind all the text. The `--correct-text-visibility` partial solve this problem, but it may not work perfectly on all inputs.

### Writing mode fonts
Text go top-bottom, right-left
 - HTML supports such fonts?
 - How to position them in HTML?
   - CSS rule `writing-mode` is not yet well supported.

### Font size rounded by browsers
10.3pt text are usually rendered as 10pt text in web browsers, which often causes inaccuracy in the layout.

Possible solutions:
- Find the nearest fraction number (i.e different multiplier for different font sizes).
- See if the `text-rendering` CSS properties is useful.

Relevant links:

- http://meyerweb.com/eric/thoughts/2010/02/10/rounding-off/
- https://developer.mozilla.org/en-US/docs/Web/CSS/text-rendering
