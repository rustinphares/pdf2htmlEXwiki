# dummy

## Why did you start this project?

 - For FUN

## What's the ultimate goal of pdf2htmlEX?

 - To make me happy
 - To be possibly useful for others

## Which languages are used in pdf2htmlEX?
  
 - C++ (most part)
 - C (wrapper of Fontforge)
 - HTML (output)
 - CSS (complicated enough to be considered as a language)
 - Javascript (UI actions/effects)
 - Python (scripts for testing / packaging)

## pdf2htmlEX is really great! What shall I do?

 - Add a star in the [project page](http://github.com/coolwanglu/pdf2htmlEX), at the top-right corner.
 - Tell others about it, using your social power.
 - Use it and enjoy it.
 - Please consider [making a donation](http://coolwanglu.github.com/pdf2htmlEX/donate.html).

## pdf2htmlEX sucks! What shall I do?

 - Tell me what's wrong.
 - Technical complaints are welcome.
   - Emotional are not.

## pdf2htmlEX doesn't work for my pdf file!

 - Bug reports are always welcome, please file an issue with the link to the broken pdf file.
 - However there are several exceptions when the bug cannot be fixed in time (or at all)
   - The file does not follow the PDF standard (it might still be displayed correctly in PDF viewers)
   - Something wrong with libraries used by pdf2htmlEX (poppler / fontforge)

## How about feature requests?

  - Keep in mind that pdf2htmlEX has been provided as a toy for hackers, not a user-friendly tool.
  - Patches are as welcome as bug reports.
  - Try to convince me that the feature is attractive/challenging/important.
   - I will put it into the TODO list.
   - There's little chance that feature requests about user interface will be accepted.
  - Propose a feature Commission (see below)

## <div id="feature_commission">Feature Commission</div>

 - Proposed a feature and price
   - Send me an email
   - OR file a new Issue on GitHub
   - OR comment on an existing feature request
 - I will confirm before I start to implement

## I cannot compile it!

 - Make sure you have installed all required packages (and headers).
 - Make sure poppler has been compiled with --enable-xpdf-headers
   - Especially when you see something about goo/GooString.h
 - Make sure C++11 is supported by your compiler
 - Fontforge has not been linking friendly until recent:
   - Git version is recommended
   - If there's something wrong about 'spiroentrypoints.h', install header files of libspiro
   - If there's something wrong about 'undefined reference of Py_xxx', install header files of python-2.x
   - If there's something wrong about 'libintl.h', install gettext and set your system include path accordingly.

## 'Cannot open the manifest file'
 - Run 'sudo make install' or 'make install', depending on your environment.

## There is no image generated

 - Make sure you did not specify --process-nontext 0
 - Make sure libpng (and headers) is installed BEFORE poppler was compiled.

## The generated HTML file looks ugly

Recommended web browsers
 - IE9 / Firefox / Opera / Chrome (Windows)
 - Firefox / Chrome / Opera (Linux/Mac)
 - Dolphin Browser (Android)

## The generated HTML file freezes my Firefox
 
 - Don't zoom in too much
 - Use a smaller value for --font-size-multiplier

## Something wrong with text in the generated HTML file, I cannot even read them
 
 - Install ttfautohint and run pdf2htmlEX with --external-hint-tool=ttfautohint
 - Try --auto-hint 1 carefully, which is experimental now.

## I got incorrect text after copy & paste

 - try run with --tounicode 1

## Generated text are too small to read

 - try run with --zoom 2

## Images are blurred

 - try run with --hdpi 288 --vdpi 288
