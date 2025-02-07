- [General](#general)
- [Text and Font](#text-and-font)
- [Image](#image)

<div id="general"></div>
## General

### Languages used in pdf2htmlEX

 - C (Fontforge wrapper)
 - C++ (most part)
 - CSS (output: format / effects)
 - HTML (output: contents)
 - Java (optimization)
 - JavaScript (output: UI / effects)
 - Python (scripts)
 - Shell (scripts)

### Libraries used in pdf2htmlEX
 - Poppler (PDF parsing)
 - Fontforge (font manipulation)
 - jQuery (for the default UI)
 - closure-compiler (JavaScript optimization)

### pdf2htmlEX doesn't work for my pdf file

 - Bug reports are always welcome, please file an issue with the link to the broken pdf file.
 - However there are several exceptions when the bug cannot be fixed in time (or at all)
   - The file does not follow the PDF standard (it might still be displayed correctly in PDF viewers)
   - Something wrong with libraries used by pdf2htmlEX (poppler / fontforge)
   - There are a few technical limitations of pdf2htmlEX. See [this page](https://github.com/pdf2htmlEX/pdf2htmlEX/wiki/Limitations)

### I want more features!
 - Create a patch, or hire someone to do so.
 - Best hackers do not work for free.
 - But great ideas are more valuable than money.

### 'Cannot open the manifest file'
 - Run `sudo make install` or `make install`, depending on your environment.

### The generated HTML file freezes my Firefox

 - Don't zoom in too much
 - Use a smaller value for `--font-size-multiplier`

### The generated HTML file looks awful

Check if your browser meets the [requirements](https://github.com/pdf2htmlEX/pdf2htmlEX/wiki/Browser-Requirements).

### The generated HTML file is too large

 - File embedded in HTML are encoded in Base64, whose size is 1/3 larger. Embedding can be disabled using the `--embed` option.
 - Try to disable embedding external fonts. [Learn more...](https://github.com/pdf2htmlEX/pdf2htmlEX/wiki/Font-Files#external-fonts)
 - There is built-in compression support in PDF, but no such feature in HTML. Fortunately most HTTP servers support compression (gzip/deflate), and you may check the actually network communication cost by compressing the HTML file with `gzip`, which is usually smaller than PDF.

***
<div id="text-font"></div>
## Text and Font

### Text are correct but not readable

 - Install ttfautohint and run pdf2htmlEX with `--external-hint-tool=ttfautohint`
 - Try `--auto-hint 1` carefully, which is experimental now.

### I got incorrect text after copy & paste

 - try run with `--tounicode 1`
 - Make sure you CAN copy & paste with a PDF viewer
   - If you can not, neither can pdf2htmlEX

***
<div id="image"></div>
## Image

### There is no image generated

 - Make sure you did not specify `--process-nontext 0`
 - Make sure libpng (and headers) is installed BEFORE poppler was compiled.

### Generated text are too small to read

 - try run with `--zoom 2`

### Images are blurred

 - try run with `--hdpi 288 --vdpi 288`
