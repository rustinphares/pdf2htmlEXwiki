# dummy

## Non-technical

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

### <div id="help">How can I help pdf2htmlEX</div>
 - Add a star in the [project page](http://github.com/coolwanglu/pdf2htmlEX), at the top-right corner.
 - Tell others about it, using your social power.
 - Suggest interesting PDF files which can be used as demos.
 - Use it and enjoy it.
 - Find bugs and report them.
 - [Make a donation](http://coolwanglu.github.com/pdf2htmlEX/donate.html).

### <div id="install-windows">How to install pdf2htmlEX on Windows</div>
 - There is no binary package so far, so do not expect an easy click-and-install. There are 2 options:
  - Install Linux in a virtual machine, then install pdf2htmlEX
  - Build the source through Cygwin (recommended) or MinGW
 - If you can help maintain binary packages for Windows, or at least find an easy way to do this, please contact me. 

***

## Pitfalls 

### <div id="compile">I cannot compile pdf2htmlEX</div>

 - Make sure you have installed all required packages (and headers), see Readme.
 - Make sure poppler has been compiled with --enable-xpdf-headers
   - Especially when you see something about goo/GooString.h
 - Make sure C++11 is supported by your compiler
 - Fontforge has not been linking friendly until recent:
   - Git version is recommended
   - If there's something wrong about 'spiroentrypoints.h', install header files of libspiro
   - If there's something wrong about 'undefined reference of Py_xxx', install header files of python-2.x
   - If there's something wrong about 'libintl.h', install gettext and set your system include path accordingly.

### 'Cannot open the manifest file'
 - Run 'sudo make install' or 'make install', depending on your environment.

### There is no image generated

 - Make sure you did not specify --process-nontext 0
 - Make sure libpng (and headers) is installed BEFORE poppler was compiled.

### <div id="ugly">The generated HTML file looks ugly</div>
 
Check if your browser meets the [requirements](https://github.com/coolwanglu/pdf2htmlEX/wiki/Browser-Requirements).

### The generated HTML file freezes my Firefox
 
 - Don't zoom in too much
 - Use a smaller value for --font-size-multiplier

### Something wrong with text in the generated HTML file, I cannot even read them
 
 - Install ttfautohint and run pdf2htmlEX with --external-hint-tool=ttfautohint
 - Try --auto-hint 1 carefully, which is experimental now.

### I got incorrect text after copy & paste

 - try run with --tounicode 1
 - Make sure you CAN copy & paste with a PDF viewer

### Generated text are too small to read

 - try run with --zoom 2

### Images are blurred

 - try run with --hdpi 288 --vdpi 288
