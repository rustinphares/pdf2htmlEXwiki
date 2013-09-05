- [General](#general)
- [Text and Font](#text-font)
- [Image](#image)

## <div id="general">General</div>

### Languages and libraries used in pdf2htmlEX
  
 - C++ (most part)
 - C (wrapper of Fontforge)
 - HTML (output)
 - CSS (complicated enough to be considered as a language)
 - Javascript (UI actions/effects)
 - Python (scripts for testing / packaging)
 - Poppler (PDF parsing)
 - Fontforge (font manipulation)
 - jQuery (for the default UI)

### pdf2htmlEX doesn't work for my pdf file

 - Bug reports are always welcome, please file an issue with the link to the broken pdf file.
 - However there are several exceptions when the bug cannot be fixed in time (or at all)
   - The file does not follow the PDF standard (it might still be displayed correctly in PDF viewers)
   - Something wrong with libraries used by pdf2htmlEX (poppler / fontforge)
   - There are a few technical limitations of pdf2htmlEX. See [this page](https://github.com/coolwanglu/pdf2htmlEX/wiki/Limitations)

### <div id="feature_commission">I want more features!</div>
 - Create a patch, or hire someone to do so.
 - Best hackers do not work for free.
 - But great ideas are more valuable than money.

<!--
### <div id="install-windows">How to install pdf2htmlEX on Windows</div>
 - There is no binary package so far, so do not expect an easy click-and-install. There are 2 options:
  - Install Linux in a virtual machine, then install pdf2htmlEX
  - Build the source through Cygwin (recommended) or MinGW
 - If you can help maintain binary packages for Windows, or at least find an easy way to do this, please contact me. 
-->

### 'Cannot open the manifest file'
 - Run 'sudo make install' or 'make install', depending on your environment.

### The generated HTML file freezes my Firefox
 
 - Don't zoom in too much
 - Use a smaller value for --font-size-multiplier

### <div id="ugly">The generated HTML file looks awful</div>
 
Check if your browser meets the [requirements](https://github.com/coolwanglu/pdf2htmlEX/wiki/Browser-Requirements).

***

## <div id="text-font">Text and Font</div>

### Text are correct but not readable
 
 - Install ttfautohint and run pdf2htmlEX with --external-hint-tool=ttfautohint
 - Try --auto-hint 1 carefully, which is experimental now.

### I got incorrect text after copy & paste

 - try run with --tounicode 1
 - Make sure you CAN copy & paste with a PDF viewer
   - If you can not, neither can pdf2htmlEX

***

## <div id="image">Image</div>

### There is no image generated

 - Make sure you did not specify --process-nontext 0
 - Make sure libpng (and headers) is installed BEFORE poppler was compiled.

### Generated text are too small to read

 - try run with --zoom 2

### Images are blurred

 - try run with --hdpi 288 --vdpi 288
